---
title: "Nautilus SSH connection over VPN"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by protenniser on 2007-09-04
Hi all,
I have a problem at making nautilus connect to a server with ssh option.
What I want to do is have a graphical connection with another computer. (no gptf is not enough)
In order have any connections with this computer, I have to first make a vpn connection. I make it via network manager applet and its vpn plug-in, there is no problem. (Btw if a make mac id filtering from my rooter I can't make vpn connections any more, is this a bug? Is there a solution?) After that I make Places/Connect to Server and than write the ip address, user name, and password of that server. The connection than appears in my desktop. I double click, a dialogue opens saying me that connecting to ........ If you want to cancel. After that I wait, and nothing nothing totally happens. No connection, or error messages, or no nautilus that open the folder I wanted. I was able to make this right on Edgy, but now I use feisty fawn and it didn't work form the first time. I am hopeless so gurus, please help. 
Thanks for all help, regards....

---

### Post by protenniser on 2007-09-04
Some updates about my problem:
1-) After I create the connection, if I try to double click on the icon, I am helpless nothing happens (still the same)
2-) After I create the connection, if I go to Places/and then if I choose the newly created connection, this time it waits and gives me the error "time-out" (new)
3-) If I fire up a file browser and there I write ssh://kmuslu@host then it gave me that stupid error because of the changing of the key ring that have been mentioned in the forum. (new)
4-) &#305; have deleted the .ssh_knownkeys (it was something like that, I only delete the text inside it) and I make number 3, then voilà I can connect!
At least know I can connect in a painful way :). However I am still open to all suggestions.

---

