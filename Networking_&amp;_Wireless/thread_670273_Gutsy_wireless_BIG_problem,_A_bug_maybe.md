---
title: "Gutsy wireless BIG problem, A bug maybe?"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by seng1978 on 2008-01-17
Short story:

Wireless connects and after a few minutes it disconnects.
Entering NM shows two wired connections?
in terminal after typing a command such as sudo ifconfig eth0 down
or sudo whatever and ENTER it jumps to next line and does nothing
cant close the terminal, cant open system monitor to force quit or kill process
opening a new terminal same thing
then system hangs i can move my mouse though
but cant restart either
cause typing something like sudo shutdown -r now
doesnt do anything just sits there and wait
SO hold Power button five seconds and turn back on


Long story:

I was googlin around bout this problem some people wrote scripts to detect wthether NM disconnects from wireless or something like that.
Other say I should use roaming instead of manual setup
I did..same problem as short story!
I thought maybe its my wireless card and its restricted driver ABG 3945
I turned it off and pluged in my PCMCIA wireless g D-Link caRD.
sEEMED to work longer maybe an hour or two.
Then still hangs like short story.

So it must be gutsy huh?
Wired connection 24 hours no problem at all.
However, remember I turned off the restricted driver for 3945?
After I encountered that the problem wont be solved after using a different wireless
card I turned back on the restricted driver for 3945.
Then I was doing some ftp transfer and samba fileshare etc. I had a connect from 8pm till 8 am in the morning(got to got to work at 8am so i had to turn off my computer)
I was transferring files from an ftp server 5gigs. It went smooth and no hang or whatsoever. Problem seemed to be solved.
Well not quite. After I am back from work I connected to wireless ap again and transferred a 900mb file to my samba server. As expected and it hanged again.
Thats why I am writing here. 

My point is, it seems that after enabling the restricted driver(restart required of course)
for 3945 the wireless seemed to work as it suppose to work, flawlessly.

so any suggestions other than reinstall computer..

thanks in advance

seng

---

### Post by cendant on 2008-01-17
aha, so it is not only me.

Wired connection in Gutsy worked for me, but Wi-Fi at home kept dropping connection or slowing to a hold. Only reboot helped

The same Intel Wifi adapter on Dell XPS 1330.

I returned to Windows Vista until May. In my observation, the developers break wireless every second release, then fix it then break again. Since I do not want Edgy, I will wait for 8.04 or until I find a fix.

---

### Post by Hightide on 2008-01-17
Sometimes various wireless drivers and  NM clash causing weird problems

Try WICID as an alternative instead of networkmanager.  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) 

Code:
sudo apt-get remove network-manager; 

sudo apt-get install wicd;

make sure you remove NM before installing wicid

hope this helps

:)

---

### Post by cendant on 2008-01-17
Found solution by Dell

Ubuntu 7.10/Issues/ipw3945 Wireless Network Module Issues
From DellLinuxWiki
< Ubuntu 7.10
Jump to: navigation, search

Description: When using the ipw3945 wireless module, the network connection can drop or lockup during heavy transfer rates. 
Systems Affected: Inspiron 1420n 
Impact: Wireless connection drops. Data transfer stops. 
Workaround: Use network module iwl3945 instead. 

Create a file called /etc/modprobe.d/blacklist-ipw3945 and add: 

blacklist ipw3945
Add to /etc/modules: 

iwl3945
Reboot. After the system restarts, verify that the module iwl3945 (and not ipw3945) is loaded: 

$ lsmod | egrep 'Module|iwl|ipw'
You should see an output that looks like: 

Module                  Size  Used by
iwl3945                88168  0
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
As seen, only the iwl3945 module is loaded. 

Retrieved from "http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues"





OR this might help


sudo apt-get install linux-ubuntu-modules-2.6.22-14-386





There is a similar bug 


[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045)





Let's try again

---

### Post by seng1978 on 2008-01-17
hey..thanks for quick respnse

i forgot to mention that I tried wicd already
same thing as NM

so i put wicd aside and use NM again.

---

### Post by seng1978 on 2008-01-17
hey thanks for the modprobe thing
i read it too to use iwl instead of ipw
but i couldnt get behind their weird instructions untill cendant explained to me(cendant, thanks for ur understanduing, u know im a noob and u wrote the instructions for a noob)

w\i try this for now
im copying a 5 gig file now to samba server and ill check my wireless connection tomorrow morning.
me going to sleep now
if its till up tomorrow

I love you cendant, 

if not

thanks for your help anyways cendant, i appreciate it



good nite


ill let you guys know the result tomorrow

---

### Post by seng1978 on 2008-01-17
this morning i checked on my computer...same thing...
hung...Forced shutdown.

Well I really think its a bug.
As i said the only time the wireless really is stable is after enabling the restricted driver.
But I cant always restart my restricted driver in order to use wireless right?

thanks cendant for ur help
I appreciate it.

I dont really wanna switch to Vista. I tried installing skype yesterday and it gave me errror code 1603. I hate Microsoft any windows. Its just not a stable system at all.

If I would just get my wireless stable in ubuntu...

---

### Post by seng1978 on 2008-01-18
ok i just realized my wireless doesnt hang when i do nothing other than using firefox.
transfering via ftp or samba, watching a movie from a samba share, chatting to  ubuntu staff on irc all make my laptop hang....

need help

anyone got the ubuntu 8.04 yet? :)

---

