# Interview Questions and Answers

**1. What is an open port?**  
A port where a service is listening and accepts connections. When a SYN packet is sent to it, the device replies with SYN-ACK.

**2. How does Nmap perform a TCP SYN scan?**  
Nmap sends a SYN packet to each port. A SYN-ACK reply means the port is **open** (Nmap then sends RST and does not complete the handshake, so it is called a half-open or stealth scan). A RST reply means **closed**. No reply or an ICMP error means **filtered** (a firewall is blocking it).

**3. What risks are associated with open ports?**  
They increase the attack surface. Attackers can exploit vulnerable or outdated services, guess passwords (brute force), steal information, or use them to enter the network and spread malware.

**4. Explain the difference between TCP and UDP scanning.**  
TCP is connection-oriented (three-way handshake), so open and closed ports give clear replies and scanning is fast (`-sS`). UDP is connectionless with no handshake, so open ports often send no reply, closed ports return ICMP "port unreachable", results are often "open|filtered", and the scan is slower (`-sU`).

**5. How can open ports be secured?**  
Close unused ports and services, use a firewall, keep software patched, use strong authentication, bind services to localhost where possible, use a VPN or network segmentation, and monitor with an IDS.

**6. What is a firewall's role regarding ports?**  
A firewall allows or blocks traffic by port, IP address and protocol based on rules. It stops unwanted inbound connections so that services are not exposed. Blocked ports appear as "filtered" in a scan.

**7. What is a port scan and why do attackers perform it?**  
A port scan checks which ports on a host are open. Attackers do it as reconnaissance, the first step of an attack, to find live hosts and running services and look for vulnerable ones. Defenders scan their own systems to find and fix exposure.

**8. How does Wireshark complement port scanning?**  
Nmap shows the result (open, closed, filtered). Wireshark shows the actual packets (SYN, SYN-ACK, RST), so you can see how the scan works, verify the results and detect scans on a network.
