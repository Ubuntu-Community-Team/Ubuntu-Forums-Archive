---
title: "ubuntu 804 firefox  connect  internet problem"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by tedchyn on 2009-12-11
I installed vmware workstation and ubunto804 iso on window xp desktop. after installation. 
 
1. xp window side - contral panel -> internet connections show following 4 are connected. 
local area connection 3
vmnet1 - for host only
vmnet8 - for nat 
1394 connection 
 
window IE can connect to internet ([www.yahoo.com]("http://www.yahoo.com")).
 
2. ubunto side
ipconfig show eth0 has inet of 192.168.252.129
 
vmware network editor show Wmnet0, WMnet1 and WMnet8 all DHCP enabled
and WMnet8(nat) is checked during installation
 
all ip addresses can be seen from ubunto side using ping
 
##nslookup [www.yahoo.com]("http://www.yahoo.com") resolve same ip as from XP side
 
 
BUT When I use firefox for [www.yahoo.com]("http://www.yahoo.com") I got 
Failed to connect can't establish connection to server [www.yahoo.com]("http://www.yahoo.com")
 
question,
 
1. Is this a firewall problem (window xp is firewall protected) 
Or this is related to firefox browser(plugin related) 
Or this is cause by something else unrelated to problems described above
 
2. why nslookup see yahoo.com and firefox cannot ?
 
thanks a lot ted

---

### Post by ukripper on 2009-12-11
Have you got proxy enabled? in you IE check this location go to Tools-->internet options-->Connections-->LAN settings. see if proxy is enabled there and not in your firefox.

---

### Post by tedchyn on 2009-12-11
> **ukripper said:**
> Have you got proxy enabled? in you IE check this location go to Tools-->internet options-->Connections-->LAN settings. see if proxy is enabled there and not in your firefox.
 
 
proxy is enabled in IE. How do I enable proxy in firefox ?

---

### Post by ukripper on 2009-12-11
in firefox click on File-->Import and then follow the wizard Select Microsoft Internet Explorer--> Next -->Just tick Internet options-->Next

this should do it for you.

---

### Post by tedchyn on 2009-12-11
> **ukripper said:**
> in firefox click on File-->Import and then follow the wizard Select Microsoft Internet Explorer--> Next -->Just tick Internet options-->Next
 
this should do it for you.
 
firefox ->file -> import -> import wizard give following message
 No programs that contanint bookmarks, history or password data could be found

---

### Post by ukripper on 2009-12-11
> **tedchyn said:**
> firefox ->file -> import -> import wizard give following message
 No programs that contanint bookmarks, history or password data could be found

My mistake I assumed you wanted to import in windows  firefox  not in ubuntu's firefox.

Now you have to check your current proxy settings in IE and put same proxy settings in ubuntu's firefox:
Tools-->options-->Network-->settings.Put your proxy settings you can see in your IE in here.

---

### Post by tedchyn on 2009-12-11
> **ukripper said:**
> My mistake I assumed you wanted to import in windows firefox not in ubuntu's firefox.
 
Now you have to check your current proxy settings in IE and put same proxy settings in ubuntu's firefox:
Tools-->options-->Network-->settings.Put your proxy settings you can see in your IE in here.
 
I have firefox 3.0.1 and mozilla firefox =>tools I have 
 
         web search , downloads, add, error consolte, page info (NO OPtions under tools).

---

### Post by ukripper on 2009-12-11
> **tedchyn said:**
> I have firefox 3.0.1 and mozilla firefox =>tools I have 
 
         web search , downloads, add, error consolte, page info (NO OPtions under tools).

Go to Edit-->Preferences-->Network-->Settings

---

### Post by tedchyn on 2009-12-11
> **ukripper said:**
> Go to Edit-->Preferences-->Network-->Settings
It is under
 
firefox=>edit =>preferences => network =>settings => use system porxy stting is checked. 
 
I assume this is the same as IE => IE has use proxy server for your LAN checked.
 
 
I changed system proxy setting to manual proxy.
 
http proxy : proxy      port:8080 same as IE and IT Worked.
 
 
 
thanks a log

---

### Post by ukripper on 2009-12-11
Great! you can mark this thread as Solved from thread tools.

---

