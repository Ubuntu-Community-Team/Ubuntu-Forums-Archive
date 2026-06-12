---
title: "Proxy only works in Windows, not dapper"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Shootfast on 2007-01-13
Hi all. I've been fruitlessly trying to connect to the internet via ubuntu and a proxy. The network is set to DHCP in both windows and ubuntu (dapper), and for Windows, the only remaining step is for me to set the firefox connection settings to manual Proxy and input my proxy address and port (GOLF:8080).

Once I reboot into Ubuntu however, with those same settings i get nothing. Firefox tells me that the proxy cannot be found. Ive tried using the Network Proxy dialogue in the preferences menu, I've tried every possible combination in firefox.

I can see the network computers when I browse the network. (they are all windows computers)

Any ideas?

---

### Post by SuperMike on 2007-01-13
What happens when you go to command line on Linux by opening a Terminal console window and typing this?

$ telnet     <address of proxy>     <port of proxy>

Example:

$ telnet   golf    8080

Did you get an error? If so, then that's a clue. By the way, you can disconnect from a connected telnet session (if you didn't get an error) by doing CTRL+] and typing quit. But if you received an error, you're already out of the telnet connection.

If you got an error, then perhaps 'golf' is not translating from a name into an IP address. Find out what the IP address is and do this:

$ sudo nano /etc/hosts

and add to the bottom of this file the address like:

192.168.32.32      golf<press enter here>

(Change the above address to what golf literally is -- check for that on your proxy or ping it from Windows.)

Now try the telnet test. Another test besides telnet is:

$ sudo apt-get update
$ sudo apt-get install nmap
$ sudo nmap golf

...and this can return to you the exposed ports of the proxy and hopefully 8080 will be there.

I would reason to bet that Linux just doesn't know what 'golf' is because you haven't either set your DNS client settings properly in your network control panel (sharing the same settings as what they would be in Windows when you do 'ipconfig /all'). Without the properly assigned DNS client settings, you could also do the second technique of editing your local /etc/hosts file to put the address in there.

---

### Post by Shootfast on 2007-01-16
Thank you very much! :) That worked like a charm. I don't know why the DNS wasn't picking it up (the address was right) oh well. :D

---

