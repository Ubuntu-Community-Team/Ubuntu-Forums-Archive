---
title: "Ubuntu vs Windows - Slow internet"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by muntu on 2011-01-16
Hi

Recently made the decision to uninstall Windows XP SP3 in favour of Ubuntu 10.04. I'm almost regretting this decision and may switch back unless i can solve the problem below.

I have a 6-7yr old Fujitsu Siemens Notebook, 3.2ghz, 1GB ram, 80gb hdd. its a fairly decent machine but the instability in windows was driving me insane - i.e. blue screen of death.

I know Linux is much more stable - and opted for the Ubuntu variety (being patriotic and proudly South African :) )

My use for this particular machine is simple - its a media centre, connected to my tv from which I access the net, watch movies, etc and download stuff via Torrents and HTTP.

The machine does not have Wifi - so I have the SMC, SMCWUSB-G wifi usb adapter connected to access my router and have ADSL 384kbps line speed.

I writing this post on another Dell Windows machine because, although Ubuntu works - the internet doesnt!!!!!! *(#&U%

Heres the problem:

The Synaptic Update Manager find the updates without much problem. The downloading of packages takes significantly longer - Windows would've provided 35-40kbps but Ubuntu hovers around 4-20kbps (usually sits at 4kbps)

The torrent client, Transmission is crap - it doesnt have any bitrate at all???

I cant install uTorrent on Wine- for some reason i cant figure out how to launch a setup .exe file? any help with this?

Firefox and Chrome both load about half a page - then die, or rather the little spinner, spins but thats it?? Tried loading google.co.za and left it to spin - the search text box loaded in the correct place on the page but nothing else - for over 4 hours until i just closed the tab??

The behaviour was ok when i first installed - after the first software update and then installing wine - it died? 

It seems to me that Ubuntu knows its connected to the internet (the icon at the top has 60% strength - although the router is 3 metres away without walls in between), but its decides to forget to use the connection.

Unfortunately Windows has never given me this problem. i need this machine to be a media centre - I'm fine with Ubuntu, Transmission, VLC as opposed to Windows, uTorrent and GOM Media Player. 

But if it cant perform then i'll have to switch back and bear the blue screen again. oh - the other reason is this machine is permanently connected to the net 24/7 and usually when at I'm at work it does most of its downloads during the day and late at night. I preferred Ubuntu cos it wont crash - so ideally i'd still like to get this working.


PLEASE HELP!!! :)

---

### Post by [Snc] on 2011-01-16
> **muntu said:**
> 
I cant install uTorrent on Wine- for some reason i cant figure out how to launch a setup .exe file? any help with this?

in my experience some installers simply crash if you run them outside the WINE C: folder, i guess the install gets confused and rather aborts then runs, so move the utorrent installer to your WINE c: folder and it should work out of the box.

---

### Post by muntu on 2011-01-16
Thanks buddy.. will try this out - Hopefully can get GOM working on Ubuntu as well :)

Slow internet is still the dealbreaker though :(

---

### Post by AlexDudko on 2011-01-16
What's the purpose of installing the Windows version of uTorrent in Wine, while there is a linux version of the program [http://www.utorrent.com/downloads/linux]("http://www.utorrent.com/downloads/linux")?

If ipv6 is enabled it can also slow down the Internet connection.

---

### Post by [Snc] on 2011-01-16
> **muntu said:**
> Thanks buddy.. will try this out - Hopefully can get GOM working on Ubuntu as well :)

Slow internet is still the dealbreaker though :(

Well, Ubuntu isn't to blame, there can be something with your router/wireless and so on, the OS doesn't slow down your connection. So check your firewall settings, IP settings - including DNS, Quality Of Service settings, for the torrent, make sure the ports are forwarded correctly, ... actually only non-OS related settings. :} cant help you here, sorry

PS. GOM should work normally under WINE, its rated "bronze" tho ... [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6257](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6257)

---

### Post by davidmohammed on 2011-01-16
there was a problem of [slow speeds]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479283") reported with your wireless at 9.10 - however I surprised this hasnt been subsequently fixed.

Try the workaround as suggested then

iw set reg ZA 

then unplug and replug in your usb device

i.e.  ZA is the country code of south africe (at least thats what wikipedia says!)

---

### Post by squenson on 2011-01-16
Just an idea: I recently faced similar problems while being connected at my parents' place. The issue was that two computers shared the same IP address and this was apparently creating a mess. As soon as I forced one machine to use a fixed IP, everything was solved and both computers could work simultaneously without any problem.

---

### Post by [Snc] on 2011-01-16
> **squenson said:**
> Just an idea: I recently faced similar problems while being connected at my parents' place. The issue was that two computers shared the same IP address and this was apparently creating a mess. As soon as I forced one machine to use a fixed IP, everything was solved and both computers could work simultaneously without any problem.

that would be my first guess too, but look at davidmohamed's post too and see if it helps. 

I haven't had such problems tho... normaly i blamed the router and was right. Even sometimes my ISP was to blame ...

---

### Post by [Snc] on 2011-01-16
> **AlexDudko said:**
> What's the purpose of installing the Windows version of uTorrent in Wine, while there is a linux version of the program [http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)?

Sorry Alex, I didn't know there is a Linux version available, last time I checked uTorrent it was a Windows only thing. Also I read tutorials on how to run it under WINE...

---

### Post by muntu on 2011-01-16
thanks ppl!!

awesome - utorrent is sorted... 

i did set the country code, unplugged an replugged - also restarted  - its still very slow... its not that there's no internet, the issue is speed..

on this laptop - also connected to same router via wireless, (ps. this is a windows machine) the speed are perfect

to give an idea.. windows, down speed on http is about 25kbps (its during the day)

but on linux its about 1kbps and also times out.. 

gonna get a 10.10 cd tomorrow and then install that if i cant figure this out.. i'll report back :)

thanks again!

---

### Post by The Cog on 2011-01-16
Don't blame Transmission. I use it, and unless I configure speed limits on it, my 3-meg broadband gets swamped so nobody else can use it.

I would perhaps suspect your wireless connection or drivers. Are you able to test with a wired Ethernet for a while, to eliminate the wireless as a suspect?

---

### Post by The Cog on 2011-01-16
Don't blame Transmission. I use it, and unless I configure speed limits on it, my 3-meg broadband gets swamped so nobody else can use it.

I would perhaps suspect your wireless connection or drivers. Are you able to test with a wired Ethernet for a while, to eliminate the wireless as a suspect?

---

### Post by muntu on 2011-01-16
still battling

its definately Ubuntu or some setting within it that i cant locate.

the ipv6 is set on Ignore in System>Preferences>Network Connections - for both wired and wireless
also did the about:config in mozilla and disabled ipv6

re-installed chrome

Also switched off all other connected devices to the router with only the ubuntu machine connected (wired and wireless)

with all above - browsing is still painfully slow on mozilla and chrome

havent tested a torrent cos i cant even load a page.

however, (this is where it gets wierd)
i also have Virtualbox installed and an installation of Win XP SP1. it boots into windows fine and the internet speeds are the same as my other devices (mobile and other laptop)

in other words the VM Windows takes its internet connection via ubuntu to the router - but it has normal browsing speeds compared to browsing on ubuntu only????

now i'm really lost :-|

---

### Post by The Cog on 2011-01-16
That's ringing bells, something about MTU discovery or fragmentation perhaps. I wish I could remember the details, but all I can remember is that there is an IP option that Linux uses that windows doesn't, and some networks don't support it properly. If I find more, I'll get back to you.

---

### Post by davidmohammed on 2011-01-16
MTU discovery could be on the right track.

Found this [interesting article]("http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows") with a "how to diagnose".  Suggest give it a try for your wired connection.

If it does work then replace the "eth0" with "wlan0"  in the command examples.

---

