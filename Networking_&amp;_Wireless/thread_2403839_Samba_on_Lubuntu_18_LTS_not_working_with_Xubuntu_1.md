---
title: "Samba on Lubuntu 18 LTS not working with Xubuntu 16 LTS?"
date: 2018-10-16
forum: Networking &amp; Wireless
---

### Post by pandoragami on 2018-10-16
Hello all,

Not sure if the Ubuntu versions are a problem but basically I **_had_** Xubuntu and Lubuntu, both 16.04LTS running a LAN connection and Samba was fine; then I upgraded one machine to Lubuntu 18.04 LTS and Samba no longer wants to be recognized by the shares-admin in Lubuntu 18.04 LTS. When I try running the shares-admin it says I need to install samba or nfs; I tried installing samba with apt, both the server and client ( followed this answer -> [https://askubuntu.com/questions/883913/samba-startup-error](https://askubuntu.com/questions/883913/samba-startup-error)).

In the "Network Settings" app in Lubuntu 18.04 LTS there's a simple 3 tab layout with General, DNS, Hosts on top. I tried to enter the IP address of the _Xubuntu 16.04 LTS _machine along with the hostname and then rebooted both machines. After that I went into the network on the Lubuntu 18.04 LTS machine by using the file manager pcmanfm with the menu item go->network and that pops up an error saying "the specified location is not supported".

 When it says "not supported", is this because the network implementation on the Xubuntu 16.04 LTS side isn't compatible to the Lubuntu 18.04 LTS side?

Basically Samba is dead on Lubuntu 18.04 LTS and the new network software in Lubuntu 18.04 LTS isn't compatible with Xubuntu 16.04 LTS? Is that the problem? If so I'll just upgrade both machines to the newer one but you all know how tricky that is so it would be nice to have a workaround.

Thanks

---

### Post by Morbius1 on 2018-10-17
Not a Lubuntu user so I really have no idea but:

** Lubuntu apparently isn't aware that shares-admin no longer works.

** system-config-samba no longer works either. It's missing a file and it's launcher is set to use gksu which no longer exists.

> After that I went into the network on the Lubuntu 18.04 LTS machine by  using the file manager pcmanfm with the menu item go->network and  that pops up an error saying "the specified location is not supported".

 When it says "not supported", is this because the network  implementation on the Xubuntu 16.04 LTS side isn't compatible to the  Lubuntu 18.04 LTS side?
I seriously doubt it. Here's my guess: I think the "specified location" that is says is not supported is "network:///". THat means it's missing a package so I would install it - if it's already installed it will tell you so:
```
sudo apt install gvfs-backends
```

---

### Post by pandoragami on 2018-10-17
Thanks, I did install it ([COLOR=#000000][FONT=&quot]sudo apt install gvfs-backends)[/FONT][/COLOR] a short while ago but I still cannot see the shared folders on my other machine. I'm not sure where I should enter my hostname and ip-address once backends is installed ( it did end the error message popup). I tried looking in the Samba Server Configuration app (managed to get it working with this video [https://www.youtube.com/watch?v=sLy1WVxdXmY](https://www.youtube.com/watch?v=sLy1WVxdXmY)) and it doesn't seem to have anywhere to specify other computers, so I assumed the environment is setup automatically by detecting every other machine connected to the router, or at least that is how the shares-admin worked, but the hostname and ip had to be entered.

---

### Post by Morbius1 on 2018-10-17
You need to see if samba itself is broken or just host discovery.

Open a terminal on your Lubuntu machine and run:
```
pcmanfm smb://ip-address-of-the-xubuntu-machine
```

Then again with it's mDNS host name - don't forget the ".local" at the end:
```
pcmanfm smb://xubuntu-host-name.local
```
[COLOR=#0000cd]**EDIT**[/COLOR]: Looks like I'm running out of time today. I have a suggestion. If accessing the Xubuntu machine by its mDNS host name works you can just Bookmark it - if PCManFM allows that sort of thing. If not just go to your Xubuntu machine and add a file:

** Create a file at **/etc/avahi/services/samba.service**

** Add this to it:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```

It should show up when you go to Go > Network on Lubuntu.

---

### Post by pandoragami on 2018-10-17
The call in bash "[COLOR=#000000][FONT=&quot]pcmanfm smb://ip-address-of-the-xubuntu-machine" worked! The file samba.service doesn't? Do I edit the sample you gave, like the Display Name? 


[/FONT][/COLOR]

---

### Post by Morbius1 on 2018-10-18
> The call in bash "[COLOR=#000000][FONT=&amp]pcmanfm smb://ip-address-of-the-xubuntu-machine" worked![/FONT][/COLOR]
Does that mean this did not work:
```
pcmanfm smb://xubuntu-host-name.local
```
If not can you ping the xubuntu machine by that name from Lubuntu:
```
ping -c3 xubuntu-host-name.local
```

You can bookmark smb://[COLOR=#000000][FONT=&amp]ip-address-of-the-xubuntu-machine in PCManFM assuming these are all static ip addresses.[/FONT][/COLOR]

---

### Post by pandoragami on 2018-10-18
> **Morbius1 said:**
> Does that mean this did not work:
```
pcmanfm smb://xubuntu-host-name.local
```
If not can you ping the xubuntu machine by that name from Lubuntu:
```
ping -c3 xubuntu-host-name.local
```

You can bookmark smb://[COLOR=#000000][FONT=&amp]ip-address-of-the-xubuntu-machine in PCManFM assuming these are all static ip addresses.[/FONT][/COLOR]

Yeah that did work and I simply bookmarked it. It's actually easier to access the folders with the bookmark instead of using go->network. Thanks for your help, I'll consider this solved then.

---

