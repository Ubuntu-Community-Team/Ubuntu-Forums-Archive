---
title: "shutdown produce system halted message in ubuntu 9.10"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-12-01
I have a old Dell optiplex Gx1 computer which Ubuntu Jaunty 9.04 ran well. It gave shutdown problem (hang displaying "system halted" message instead of powering-off computer) but that was solved by:

1. Adding "apm power_off=1" to "/etc/modules" file 

2. Remarking out these lines in "/etc/rc0.d/S90halt" file as:
        # hddown="-h"
	# if grep -qs '^md.*active'
          /proc/mdstat
	# then
	#	hddown=""
	# fi 
and
        # netdown="-i"
	# if [ "$NETDOWN" = "no" ]; then
	# 	netdown=""
	# fi
3. Adding the following arguments to the kernel line of /boot/grub/menu.lst: noacpi acpi=off.

After making a fresh install of Karmic koala, I got the same shutdown problem but can't solve it as the grub architecture was fundamentally changed in ubuntu 9.10. There is no /boot/grub/menu.lst file. I did however tried :

1. changing "/etc/modules" file appending "apm power_off=1"

2. Remarking out those afore-said lines in "/etc/init.d/halt" file.

3. Changing GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="noacpi acpi=off acpi=force apm power_off=1".Saved, ran "update-grub" in terminal, rebooted.

4."sudo shutdown -h now" in terminal

5."sudo shutdown -h -P now" in terminal

6. Adding the following line to the /etc/init.d/halt file: rmmod snd-hda-intel

7. Changing the following lines of the /etc/rc6.d/S40umountfs file: replaceing fstab-decode umount -f -r -d $WEAK_MTPTS with fstab-decode umount -r -d $WEAK_MTPTS and fstab-decode umount -f -v -r -d $WEAK_MTPTS with fstab-decode umount -v -r -d $WEAK_MTPTS

8.Changing the following line of the /etc/default/grub file: GRUB_CMDLINE_LINUX="" to: GRUB_CMDLINE_LINUX="reboot=b".

No success so far. I know that i can revert to Jaunty but that what i don't like to do. Can I get help?

---

### Post by pccat84 on 2009-12-18
Hey,  I had the same problem but is now fixed.  I followed most of you steps to get it done.  I will describe that later.

First i am using Kubuntu 9.10 on a brand new Toshiba Satellite L500D.


Here is what i did to fix the shutdown issue.

1. Adding "apm power_off=1" to "/etc/modules" file 

2. Remarking out these lines in "/etc/rc0.d/S90halt" file as:
        # hddown="-h"
	# if grep -qs '^md.*active'
          /proc/mdstat
	# then
	#	hddown=""
	# fi 
and
        # netdown="-i"
	# if [ "$NETDOWN" = "no" ]; then
	# 	netdown=""
	# fi

3. I edited the grub config.  9.10 uses grub2 which doesnt use the menu.lst file anymore. You need to 
sudo kate (or gedit)
go to /etc/default/grub

You can then edit that file and below the line talking about the splash type in:
GRUB_CMDLINE_LINUX="noacpi acpi=off acpi=force apm power_off=1"

Save the file and go back to a terminal.

In the terminal type: sudo update-grub

After this i shutdown and it actually shutdown.

The only problem i had with this is that before i added acpi=force from step 3 my touhpad mouse would work but the sound buttons and volume control would not work.  After i added that everything but the touchpad works.  ARRGGGHHH.  Oh well.  I had issues with the realtek 8192se wan working as well. Got that fixed too.  If you need to reply with that as well i can.  

Hope this works for you.

---

### Post by joes7 on 2009-12-18
> **pccat84 said:**
> Hey,  I had the same problem but is now fixed.  I followed most of you steps to get it done.  I will describe that later.

First i am using Kubuntu 9.10 on a brand new Toshiba Satellite L500D.


Here is what i did to fix the shutdown issue.

1. Adding "apm power_off=1" to "/etc/modules" file 

2. Remarking out these lines in "/etc/rc0.d/S90halt" file as:
        # hddown="-h"
    # if grep -qs '^md.*active'
          /proc/mdstat
    # then
    #    hddown=""
    # fi 
and
        # netdown="-i"
    # if [ "$NETDOWN" = "no" ]; then
    #     netdown=""
    # fi

3. I edited the grub config.  9.10 uses grub2 which doesnt use the menu.lst file anymore. You need to 
sudo kate (or gedit)
go to /etc/default/grub

You can then edit that file and below the line talking about the splash type in:
GRUB_CMDLINE_LINUX="noacpi acpi=off acpi=force apm power_off=1"

Save the file and go back to a terminal.

In the terminal type: sudo update-grub

After this i shutdown and it actually shutdown.

The only problem i had with this is that before i added acpi=force from step 3 my touhpad mouse would work but the sound buttons and volume control would not work.  After i added that everything but the touchpad works.  ARRGGGHHH.  Oh well.  I had issues with the realtek 8192se wan working as well. Got that fixed too.  If you need to reply with that as well i can.  

Hope this works for you.
Cheers. If I get this problem, I know how to fix it.

---

### Post by t_k_majumdar on 2009-12-24
I am glad that my post helped someone to solve their shutdown problems. However, these steps has not helped me. This was the reason to start this new thread.

I found this problem to be widespread among linux distributions installed on old computers as far as my experience goes. Debian 5.03, Puppy Linux 4.3.1, Fedora 12, Ubuntu 9.04 and 9.10 - all failed to shutdown my computer. Only exception is KNOPPIX 6.2 running live from DVD. It gave a clean shutdown. Next best are Puppy Linux versions earlier than 4.3.1. All these are capable of shutting down computer neatly without any tweaking. Puppy 4.3.1 needed two small tweaking to get the problem solved while ubuntu jaunty jackalope needed heavy tweaking to fix the problem.

I am still looking forward to suggestions for fixing it for ubuntu karmic koala.

Thank you.

---

### Post by pdrizzle on 2010-01-08
> **pccat84 said:**
> Hey,  I had the same problem but is now fixed.  I followed most of you steps to get it done.  I will describe that later.

First i am using Kubuntu 9.10 on a brand new Toshiba Satellite L500D.


Here is what i did to fix the shutdown issue.

1. Adding "apm power_off=1" to "/etc/modules" file 

2. Remarking out these lines in "/etc/rc0.d/S90halt" file as:
        # hddown="-h"
	# if grep -qs '^md.*active'
          /proc/mdstat
	# then
	#	hddown=""
	# fi 
and
        # netdown="-i"
	# if [ "$NETDOWN" = "no" ]; then
	# 	netdown=""
	# fi

3. I edited the grub config.  9.10 uses grub2 which doesnt use the menu.lst file anymore. You need to 
sudo kate (or gedit)
go to /etc/default/grub

You can then edit that file and below the line talking about the splash type in:
GRUB_CMDLINE_LINUX="noacpi acpi=off acpi=force apm power_off=1"

Save the file and go back to a terminal.

In the terminal type: sudo update-grub

After this i shutdown and it actually shutdown.

The only problem i had with this is that before i added acpi=force from step 3 my touhpad mouse would work but the sound buttons and volume control would not work.  After i added that everything but the touchpad works.  ARRGGGHHH.  Oh well.  I had issues with the realtek 8192se wan working as well. Got that fixed too.  If you need to reply with that as well i can.  

Hope this works for you.

step #2 is not necessary.  i didn't do this step.  after doing 1 & 3, i restarted, then shutdown successfully with no hang.

---

### Post by mithunmd87 on 2010-02-07
> **pdrizzle said:**
> step #2 is not necessary.  i didn't do this step.  after doing 1 & 3, i restarted, then shutdown successfully with no hang.

Same problem as above. When I follow steps 1, 2 and 3, my screen resolution decreases from 1280x1024 to 1024x728 and the system hangs up within a few minutes of booting into GNOME. If I follow only steps 1 and 3, I can boot into GNOME, but the "System Halted" problem persists. Any suggestions?

---

### Post by dpc525 on 2010-08-22
in steps 3
quote: go to /etc/default/grub

[B]You can then edit that file and below the line talking about the splash type in:
GRUB_CMDLINE_LINUX="noacpi acpi=off acpi=force apm power_off=1"[/B]

try to cut off **acpi=force**,type in:
**GRUB_CMDLINE_LINUX="noacpi acpi=off apm power_off=1"**

refer to:[http://forum.ubuntu.org.cn/viewtopic.php?f=139&t=198151](http://forum.ubuntu.org.cn/viewtopic.php?f=139&t=198151)

---

