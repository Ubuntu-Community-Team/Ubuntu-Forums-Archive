---
title: "what is the default vendor class identifier ?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by kylegio on 2008-10-13
just need to know what the default vendor class ID is in ubuntu. i havn't been able to figure out. anyone know?
thanks
Kyle

---

### Post by Ayuthia on 2008-10-13
Can you give an example of what you are trying to find?  I don't think that I am following.  I am not understanding about which vendor class id you are trying to find.

---

### Post by kylegio on 2008-10-13
sorry my bad, what i'm looking for is the DHCP vendor class.
in windows its hard wired in to be "MSFT 5.0", which is bad for me because it allows the DHCP server to know my operating system. i dual boot between windows and linux and id like to change what my dhcp vendor class in windows to match what it is in linux. 

im trying to avoid OS fingerprinting. my network enforces some crazy rules on windows machines, ive made many changes to my windows system and im almost there but this is the one thing left thats a giveaway that im using windows.


i'm just trying to figure out what to change it to, all of my other info has been changed to appear as a ubuntu distribution

---

### Post by muzzol on 2009-07-29
not sure if this is still usefull for anyone, i just landed in this thread right now :)

the option to send this information is

[B]vendor-class-identifier
[/B]
and is defined in file, dhclient.conf, usually **/etc/dhcp3/dhclient.conf**

by default is NOT established, so dhcp server dont receive anything, but you can set any string you want, just add:

```
send vendor-class-identifier "jaunty";
```


to your file.

---

