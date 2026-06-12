---
title: "3945 iwlwifi fails when idle - No STA entry for own AP"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Andrew-buntu on 2008-04-27
I upgraded to Hardy Heron a few weeks ago when it was in Beta.  At that time, my old ipw3945 drivers got swapped out for the new iwlwifi modules in the kernel.  Now my wireless connections dies pretty often.  I can bring it back up by typing "sudo /etc/init.d/networking restart" into a terminal.  But I'd rather not have to do that all the time as ipw3945 worked flawlessly for me.  I was hoping this would be fixed before 8.04 was released.
Anyone else have an idea how to fix this problem?  I see a few other people with the same issue but the Intel 3945 wireless chips are incredibly popular so I'm surprised not to see dozens of other folks with the same problem.  Are there other people running Hardy Heron with the 3945 that AREN'T having this problem?  I'd appreciate any input.
I get this entry in dmesg a dozen times when the failures happen:
eth1: No STA entry for own AP <My router's MAC Address>

Thanks for your help.

---

### Post by chili555 on 2008-04-27
I have no problem with my iwl3945. Some people have solved problems with:```
sudo apt-get install linux-backports-modules-hardy-generic
```Let us know if that helps.

---

### Post by Andrew-buntu on 2008-04-27
I installed the modules, I'll report back in a few days and let you know whether the problem went away.  Thanks for your help.

The odd thing was that after I updated to the backported modules, my router immediately went offline.  I was going nuts because I couldn't ping anything.  After discovering I could still talk to my router's web administration service, I rebooted it and now I'm up and running.

But if I try to manage my wireless through the network monitor applet, I'm told "The interface does not exist".  It shows up fine in iwconfig though and the icon in the task bar functions fine outside of that message.  I can even go in through Systems > Administration > Network and adjust my settings.  Weird. :???:

UPDATE: Nope, still having the same problem.  After the wireless goes idle, I get that error and am forced to restart the connection.  Power management is off according to iwconfig.

Anyone else find a fix for this issue?  The backports didn't do it.

---

### Post by pjfl on 2008-05-04
I have this shell script function running in a terminal window it *seems* to be keeping the iwl3945 driver from disassociating from the AP

ping_loop() {
   while [ TRUE ]
   do
      date
      ping -c 1 <your internet gateway IP address>
      sleep 10
   done
}

This can be done with just a ping command but I like to see the date time stamps

---

### Post by szandor on 2008-05-27
> **pjfl said:**
> I have this shell script function running in a terminal window it *seems* to be keeping the iwl3945 driver from disassociating from the AP

ping_loop() {
   while [ TRUE ]
   do
      date
      ping -c 1 <your internet gateway IP address>
      sleep 10
   done
}

This can be done with just a ping command but I like to see the date time stamps

i left a continuous ping going in a terminal because i forgot to stop it but the wireless still disconnected. whenever i'm disconnected from my AP due to STA i am able to 'sudo iwlist scan' and 'ping google.com'. this gets me back online. so unless someone has found a workaround for this issue, i'm just going to write a script that greps the STA error in /var/log/syslog, compare it to the date to do this automatically. actually, i think i'll find a way to log the facility to a different log file then incorporate a script in cron every 5 minutes so if i'm remote, i don't have to wait that long to be able to ssh to my laptop. several ways to go about it i guess but if i manually run 'sudo iwlist scan; ping google.com' my wireless is back up without having to do anything silly like reboot or restart services. also, has anyone had this issue but resolved it by installing the linux-backports-modules-hardy-generic package?

---

### Post by braddock on 2008-06-15
I am also having this problem, exactly as described, on a Dell E1505n "Ubuntu Laptop" with Intel PRO/Wireless 3945ABG, using up-to-date Hardy, kernel 2.6.24-18-generic #1 SMP.

Wireless disassociates and disconnects me on average approximately once per two hours, repeatedly complaining "wlan0: No STA entry for own AP <MAC>" into the dmesg log.  Seems less common when there is traffic.  AP is a WRT54G running DD-WRT.

This laptop shipped from Dell with Feisty and I never had a problem with the wireless (or suspend).  I "upgraded" to Hardy two weeks ago and started to encounter this Wifi issue (and suspend is nearly broken, but that is another matter).  This is the E1505n with the Nvidia graphics card (a little less common).

Any advice is greatly appreciated.

---

### Post by Andrew-buntu on 2008-06-17
I haven't found an answer yet.  I get excited whenever new kernel-modules are pushed out via update-manager.  That's where you'll find your fix.

In the meantime, just add a little custom launcher to your panel that does the command
```
gksu '/etc/init.d/networking restart'
```
Make sure the single-quotes are in there.  When your wireless dies, click the launcher, type your password and your network should restart and fix the problem.  That's what I've been doing.

Hope that helps.

---

