---
title: "Edgy T43 wireless suddenly won't connect and light won't come on"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by yatesco on 2006-10-17
Hi All,

So I am running EDGY (updated a week ago) on my IBM ThinkPad T43 and for the past few days everything has been running fine, I can connect to my wireless network (ipw2200) and everything was fine.

After running for about a day or so, the connection dropped to about 1kbs (on a 4MBs cable).  /etc/init.d/networking restart sorted this out.  Anyways, this kept happening so I rebooted and now the wireless just doesn't work....the light is off and dhcp just times out.  I have (after looking at  /etc/acpi/wireless.sh) ensured it is "on" according to the kernel, and /var/log/messages correctly identifies it and states it is working....but it isn't :(

I have tried rebooting into Windows and it works fine, it is obviously something silly I have done within edgy :(

I ran Dapper for months and months and never had any problems :(

Any ideas?

Thanks.

---

### Post by baekster on 2006-10-29
Have you resolved your issue?  I have a T43 running dapper and aptitude dependency resolution seems like it might break the machine (see below). Did you have such issue?  If you didn't, do you mind sharing your apt repository list?  I just heard too many horror stories about upgrading to a new release, it makes me wanna not do it...ugh:

---------------------------------------------------------- 
...

Keep the following packages at their current version:
hpijs [2.1.7+0.9.7-4ubuntu1 (now)]
laptop-mode-tools [1.11-1ubuntu3 (now)]
libarts1c2a [1.5.2-0ubuntu1 (now)]
libgda2-3 [1.2.2-1ubuntu2 (now)]
libgmime-2.0-2 [Not Installed]
libgmime2.1 [2.1.19-0ubuntu2 (now)]
libgmime2.2-cil [Not Installed]
mdadm [1.12.0-1ubuntu5 (now)]
p7zip [4.30.dfsg-1 (now)]
python-htmlgen [2.2.2-10ubuntu3 (now)]
python-libxml2 [2.6.24.dfsg-1ubuntu1 (now)]
python2.4-htmlgen [2.2.2-10ubuntu3 (now)]
python2.4-libxml2 [2.6.24.dfsg-1ubuntu1 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
tomboy [Not Installed]
ubuntu-desktop [0.120 (now)]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -1340

---

### Post by jemodurn on 2006-10-31
I just upgraded from Dapper to Edgy and I had the same problem that T43 wireless stopped working. It was working fine in Dapper. 
In Edgy I can see the Wireless Card in the System->Administration->Networking. My light on the Thinkpad is off. 
Fn+F5 will toggle the bluetooth radio on my T43 but it won't toggle the wireless radio. 

Please HELP.

Thanks.

---

### Post by baekster on 2006-12-11
> **jemodurn said:**
> I just upgraded from Dapper to Edgy and I had the same problem that T43 wireless stopped working. It was working fine in Dapper. 
In Edgy I can see the Wireless Card in the System->Administration->Networking. My light on the Thinkpad is off. 
Fn+F5 will toggle the bluetooth radio on my T43 but it won't toggle the wireless radio. 

Please HELP.

Thanks.

Did you resolve the issue?  I recently upgraded to Edgy using the recommended way (using the GUI, not aptitude).  It worked nicely.  Everything works fine.  If you are having issues with wireless, have you checked if the moudles are being loaded?  What kind of wireless device do you have?  

run "lspci"

and run "lsmod"

I have Intel Pro Wireless 2200BG, so the matching module is ipw2200.  Check what card you have and load that module and see if you have wireless device working by 

"iwconfig"

---

### Post by aznmikex215 on 2007-01-30
this may be irrelevant, but case matters in the name of the SSID. I found this out the hard way.

my ssid is BUMBLECOUNTRY. i had it in the "Networking" tool as "bumblecountry". This appeared to disable my wireless.

eh its worth a shot :)

---

### Post by Octacube on 2007-02-23
Hello yatesco, 
 I installed Edgy yesterday and I have the identical problem you have described. Did you find the solution to your problem?
Octacube

---

