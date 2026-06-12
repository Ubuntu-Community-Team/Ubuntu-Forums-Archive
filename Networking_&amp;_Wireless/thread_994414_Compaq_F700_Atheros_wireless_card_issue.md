---
title: "Compaq F700 Atheros wireless card issue"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Chris1989 on 2008-11-26
hey guys, i am what you would call a major NOOB, i have a Compaq f700 presario, i originally installed ubuntu 8.10 on it, and it work ok, but i had to hold ctrl for it to boot up and shutdown, so i re-installed it which fixed this, i did a format for a fresh install and am currently using ubuntu 8-0-4 because i was told it is more stable or something, anyway, when i first installed it, i couldnt get the wireless card working, which is a Atheros ar242x, i looked through the forums and found something which worked, it told me to type in terminal something like, sudo get-apt ath5k, and the guy who posted it said that ubuntu has the drivers or something, but doesnt have them enabled by default, so i did that and it worked PERFECT, only problem is i cannot find the thread again, and ive been looking for weeks, and im about ready to give up on ubuntu/linux all together, i really dont want to use windows, please please please some one help me, thanks for reading

---

### Post by Chris1989 on 2008-11-26
i tried in terminal, sudo apt-get install ath5k
it says, 
sean@ubuntu:~$ sudo apt-get install ath5k
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ath5k

please someone shed some light on this, i feel im close

---

### Post by Racer-X on 2008-11-28
I, like you, was all over the board.

I had it working almost out of the box.  I only had to install the latest madwifi drivers ([http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz")) and it worked.

Then, a day or two later it seemed to break. ???

I installed the backport and restricted packages as a few different postings suggest, and, along with the ath5k driver got things working.

Then, that broke. ???

This morning I reversed everything thinking there must be some sort of problem with hal, and wanted to try to get back to square one.

I uninstalled all the stuff I'd installed (backports, restricted drivers, wicd, etc.), reinstalled all the hal stuff, network manager, etc...

Rebooted to see if it worked.  Nope.

I disabled the 'Support for Atheros 802.11 blah blah blah' hardware drivers in System -> Administration -> Hardware Drivers (you shouldn't have any ath5k if you uninstalled the backport / restricted drivers packages)

I then did a new fresh install of the above madwifi-hal version (sudo make clean, sudo make, sudo make install, sudo modprobe ath_pci, put ath_pci and wlan_scan_sta in /etc/modules)

Everything looked pretty good.  Rebooted.  Ath0 and wifi0 were showing up, but there was nothing coming from network manager tray icon. No networks showing up, but wireless *appeared* to be enabled.

Ready to pull my hair out.

I hit my wireless button that all along seemed useless in Ubuntu - it's just orange (again, I'm using a Compaq Presario C700 - or C762 to be exact) - and as I figured, nothing: no connection, just stayed orange as usual (which I'd grown used to ... don't really know why I hit it)

I went about trying to figure out my next steps and then all of a sudden, it connected to my wireless network!  It probably took 20-30 seconds from the time I hit the button to the time it linked up.

I opened up System Log (System -> Administration -> System Log), and watched after I hit this -until now- seemingly useless button.  Activity.  Hitting the button was changing states...

So for now it's working based on only having the updated madwifi.  

Try opening up System Log and look for any changes as you hit your wireless button.

I know - seems simple and stupid easy - but I'd tried nearly everything I'd seen in postings relating to this Atheros issue in Ubuntu 8.10, and until now I never saw anything seemingly conclusive when I came across this activity with the seemingly useless button. 

 And again, be patient, it takes 20 seconds or so for it to activate.

---

### Post by Chris1989 on 2008-11-28
Thanks racer x, i will try what you have suggested, i too am about ready for pulling my hair out, will let you know how it pans out for me.

---

### Post by toydolls0101 on 2009-01-20
The above worked for me.

---

### Post by pachai on 2009-03-27
"The above worked for me"

Could someone elaborate?
There were a few things people said they tried,
and it's not clear which one will provide a prompt solution.

Does anyone know if a newer version of Ubuntu 
will make this problem go away?

Thanks

---

