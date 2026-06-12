---
title: "Broadcom BCM4312"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2014-04-17
I just installed Xubuntu 12.04 on an a netbook.  OS runs great but issue with Wifi.  I installed the 3rd party drivers when installing the OS.  It asked me if i wanted to install the additional drivers and I did.  The wireless network icon now appears but I cannot use it to connect.  When right clicking on it, wireless network is greyed out.  I would like to install this on an older laptop I have also that has a broadcom chip for wireless also, but I am very inexperienced with linux wireless.  I found this link ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) but not sure how to install this.  Any suggestions will be greatly appreciated.

Thank you.

---

### Post by Navneet_Kumar on 2014-04-17
You just need to install the updates for the first time...and then it will work just fine..Hope this will solve the problem

---

### Post by windowsfree on 2014-04-17
unsure of what update you are referring to.  I did do the updates on Xubuntu and restarted the computer.  The issue persists.

Any thoughts?


Thank you.

---

### Post by mörgæs on 2014-04-17
Did you read the sticky notes?

---

### Post by windowsfree on 2014-04-17
I am not sure what you are referring to, so I guess I did not.  Sorry.  can you tell me where to find them.

---

### Post by Iowan on 2014-04-17
[Here]("http://ubuntuforums.org/showthread.php?t=2214110") is one... there may be others...

---

### Post by windowsfree on 2014-04-17
Thank you, I will work on this later today.  I appreciate all the responses.

---

### Post by chili555 on 2014-04-17
Just for the benefit of you and the searchers, the Additional Drivers tool happily and cheerfully installs the *wrong* driver in several cases. Please check the sticky and compare your pci.id. If yours requires something other than bcmwl-kernel-source, then you will need to remove the incorrect driver, as outlined in the sticky, install the correct driver or, more likely, firmware and then reboot.

The pci.id is everything; it is needed to identify the device and thereafter install the correct driver or firmware. Searchers, do not just read any old BT4 or Arch or Suse thread and read that for some obscure Broadcom that is undoubtedly not the same as yours; that you need to boil a skunk in kerosene and chant a magic incantation to get your Broadcom working. It probably won't work and you'll end up with a big mess that Iowan and mörgæs and I will spend hours undoing.

Please do not bring me your boiled skunk.

---

### Post by windowsfree on 2014-04-17
Thanks for your input.   ***[ThinkPenguin.com]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux")*** will be my next step if the above instructions do not work for my instance.

---

### Post by chili555 on 2014-04-17
> **windowsfree said:**
> Thanks for your input.   ***[ThinkPenguin.com]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux")*** will be my next step if the above instructions do not work for my instance.That would be a remote 12th or 13th step. My suggested next step is to post back and tell us what pci.id you have, what you tried, what went wrong and ask for just a little additional help. 

I am pretty confident you'll find the answer in the sticky.

---

### Post by windowsfree on 2014-04-17
Ok, do I need to do anything at this point since I installed the non-standard drivers for the Broadcom that was suggested by the OS after the install?  I do not have the computer with me at the moment so I cannot post the output of the commands.   I sincerely appreciate your assistance.

---

### Post by chili555 on 2014-04-17
> **windowsfree said:**
> Ok, do I need to do anything at this point since I installed the non-standard drivers for the Broadcom that was suggested by the OS after the install?  I do not have the computer with me at the moment so I cannot post the output of the commands.   I sincerely appreciate your assistance.It's all covered in the sticky; e.g.:> NOTE - If you have previously installed any drivers, have blacklisted or uncommented any driver files or configuration files or have done any changes whatsoever to the system to make the drivers work, you will need to undo them in order to follow this guide. We assume you are doing this from scratch and have not changed the configuration files, modules or drivers in the system in any way (apart from updating it).

For example, if you previously installed the bcmwl kernel source package, you will need to remove it by using the purge method:
```
sudo apt-get purge bcmwl-kernel-source
```But don't rely on my and your guesswork, verify your device and then proceed as outlined there.

---

### Post by windowsfree on 2014-04-17
> **windowsfree said:**
> Ok, do I need to do anything at this point since I installed the non-standard drivers for the Broadcom that was suggested by the OS after the install?  I do not have the computer with me at the moment so I cannot post the output of the commands.   I sincerely appreciate your assistance.

Here is the output from the command.

bob@bob-NETBOOK:~$ lspci -nn -d 14e4:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
bob@bob-NETBOOK:~$ ^C

---

### Post by chili555 on 2014-04-17
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="#FF0000"]14e4:4315[/COLOR]]So what does the sticky say you need for this device? Did you do it?

---

### Post by windowsfree on 2014-04-18
i installed the software and then i got a message that the wifi switch was off.  I tried moving the hardware switch to turn it on, but that did not work.  I am dual booting this for now and when i went into windows there was no issue - switch was on.  I restarted into Xubuntu and i got the message about the hardware switch.  I found on the SolydXK forums some messages about this error too.  It is not a software block.    I don't think there is much I can do.  I have a Lenovo S10 netbook that XUBUNTU  is installed on with Windows 7.  Does anyone have suggestions.


Updated info:  I found when booting the netbook if I tap the hardware switch as if to turn it on, the wireless works.  I have found this issue on other forums with the Lenovo netbook.  It seems like since this is such a big inconvienence, I may have to stick with just Windows OS on it.

it is NOT this:
[http://community.linuxmint.com/tutorial/view/1287](http://community.linuxmint.com/tutorial/view/1287)

Any suggestions welcomed.

Thank you

---

### Post by chili555 on 2014-04-18
> I don't think there is much I can do. 
....
It seems like since this is such a big inconvienence, I may have to stick with just Windows OS on it.
We aren't done until Chili says we're done. Let's see some diagnostics:```
lsmod | grep -e b43 -e wl
rfkill list all
```Thanks.

---

### Post by windowsfree on 2014-04-18
Thanks, you made me laugh.  I won't be able to do this until later today or tomorrow, so please watch for my post.   Thanks again.  We are NOT done.
I did download Xubuntu 14.04.  I may install that and attempt everything again.  I will post all steps.

---

### Post by windowsfree on 2014-04-19
here is the output from the two commands,  notice the hardblock.  I experimented with 3 other distros and this occurs on each one. when physically depressing the hardwire switch (button), nothing happens.  trying the FN+F5 key nothing happens either.  This switch and key combo works under MS Windows 7.  (also this is ver 14.04)

I appreciate your assistance

---

### Post by chili555 on 2014-04-19
Just as an experiment, please try:```
sudo modprobe -f ideapad-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by windowsfree on 2014-04-19
sorry -- no.

thanks.
[ATTACH=CONFIG]252225[/ATTACH][ATTACH=CONFIG]252226[/ATTACH]

---

### Post by chili555 on 2014-04-19
> **windowsfree said:**
> sorry -- no.

thanks.
I think you meant, "Sadly, old Chili made a mistake." Oops, sorry for my misstep.```
sudo modprobe [COLOR="#FF0000"]-r[/COLOR] ideapad-laptop
sudo rfkill unblock all
rfkill list all
```With my apologies, please try again.

---

### Post by windowsfree on 2014-04-19
no problem, i followed your steps and see attachments.

---

### Post by windowsfree on 2014-04-19
> **chili555 said:**
> I think you meant, "Sadly, old Chili made a mistake." Oops, sorry for my misstep.```
sudo modprobe [COLOR=#FF0000]-r[/COLOR] ideapad-laptop
sudo rfkill unblock all
rfkill list all
```With my apologies, please try again.

Well I have to say, that fixed it.  
Thank you.  I appreciate it very much.

---

### Post by chili555 on 2014-04-19
> **windowsfree said:**
> Well I have to say, that fixed it.  
Thank you.  I appreciate it very much.No, as I said, it isn't fixed until Chili says we're done. Let's make it persistent.```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```Also, I notice that iwl3945 is loading. Unless you *also* have an internal iwl3945 device, it isn't needed and perhaps conflicts. May we see:```
cat /etc/modules
```Thanks.

---

### Post by windowsfree on 2014-04-19
thanks, I ran the other code first and attached the output of the last command.  
thank you again.

---

### Post by chili555 on 2014-04-19
iwl3945 isn't called in /etc/modules, so where does it come from? Did you modprobe it for some reason? Is it still there after a reboot?

---

### Post by windowsfree on 2014-04-19
not sure, i didn't modprobe anything other than what y0u had me do.  
should i be doing something else?  

After rebooting I am unable to instally synaptic package manager.  I get this error:
I tried installing teamviewer also and cannot.
when i try and add other sources, I cannot choose any.
[ATTACH=CONFIG]252244[/ATTACH]

i really appreciate your assistance

---

### Post by chili555 on 2014-04-19
I think if you close Synaptic than Software Manager will work; or vice-versa.

---

### Post by windowsfree on 2014-04-20
I know this doesn't belong here but here are the exact screenshots.  I did this after restarting the computer.

Any thoughts?

Once again, thank you for your help.

---

### Post by chili555 on 2014-04-20
You are far outside my narrow area of expertise. I suggest a question here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Somebody over there has probably seen this before and has a quick fix.

---

