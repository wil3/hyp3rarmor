# Overview 

Hyp3rArmor minimizes a web  applications attack surface exposed to automated opportunistic attackers (a.k.a bots).
When this defense is applied, the web server will appear invisible to
unauthenticated users and it will be protected from most attacks on the network
stack, including zero-day vulnerabilities.

Hyp3rArmor is comprised of two primary components, a
[client](https://github.com/wil3/hyp3rarmor-client), and a 
[server](https://github.com/wil3/hyp3rarmor-server). 
For more details please read our technical report [Hyp3rArmor
Reducing Web Application Exposure to Automated Attacks](http://www.cs.bu.edu/techreports/pdf/2016-010-hyp3rarmor.pdf)

# Requirements

* You have privileges to create and modify DNS records
* You have root privileges to install Hyp3rArmor server and dependencies on the web server
* Your client allow JavaScript to be run

# Prerequisite 

Bots are classified into two categories depending on
the knowledge they poses of the target's identity. Those bots knowledgable of only the
targets IP address are referred to as IP-aware bots, where as bots knowledgable
of the targets domain name (DN), and thus also the IP address, are referred to as DN-aware bots. 

Hyp3rArmor must be configured for one of the two bots.
A [risk
assessment](http://www.cs.bu.edu/techreports/pdf/2016-010-hyp3rarmor.pdf) must
first be performed to determine which bot the website is at risk of. When in doubt configure Hyp3rArmor for DN-aware bots.

# Installation
The following instructions apply Hyp3rArmor to a web server hosted at
`your-website.com`. 

1. Create a new domain name `hidden.your-website.com`
2. Add an A/AAAA DNS record to assign the web servers IP address to `hidden.your-website.com`
3. Install the 
[Hyp3rArmor Server](https://github.com/wil3/hyp3rarmor-server) on the web server. At this point services running on the server should appear invisible  to unauthorized clients. 
3. Create a new web server, at a separate IP address, and set the A/AAAA DNS
   record of `your-website.com` to this IP address. This web server will be referred to as the visible server. 
3. Install the [Hyp3rArmor Client](https://github.com/wil3/hyp3rarmor-client) on the visible web server.
