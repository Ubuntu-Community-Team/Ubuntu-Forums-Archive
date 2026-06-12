---
title: "Error: Can't Boot in Ubuntu"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Valkyr333 on 2011-03-19
Hi, everyone.

So today, I tried to boot up my Ubuntu OS and got the following when selecting it at bootup:
```

GNU GRUB version 1.98-1ubuntu9

Minimal BASH-like line editing is supported. For the first line TAB lists possible command completions. Anywhere else, TAB lists possible device or file completions.
```

When I hit TAB to see what my options were, I got...

```
. [ badram boot cat chainloader clear configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback is ismod normal normal_exit parser.grub parser.rescue reboot rmmod root save_env search search.file search.fs_label search.fs_uuid set sleep source terminal_input terminal_output test unset
```

I don't get it. This is the second time that, while I did absolutely nothing of which I'm aware to alter Linux or any component thereof, its condition has randomly degenerated to the point where I can't even get to the login screen. Does anyone have any ideas?

Thanks,

-Val

---

### Post by Rubi1200 on 2011-03-20
Hi,
please do the following:

1. post the _full_ specifications for the computer

2. Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by Valkyr333 on 2011-03-20
Hi, thanks for responding. 

So since I'm kinda new to the details here, could you list the specifications needed? The model is a Dell Inspiron 1525 with a 14 inch screen. It has 4G RAM and a Dual-Core Processor. It's currently running Windows XP with an Ubuntu Lucid wubi-install. I'm not sure what other information is included in full specs, but once I know then I'll find them, post them and get to work on the other instructions you gave me.

Thanks again. =)

---

### Post by Rubi1200 on 2011-03-20
Are you able to boot Windows normally?

If yes, see problem #2, solution #1 in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Don't forget to apply the Permanent Fix once back in Ubuntu, including the instructions to lock the grub packages.

If you need more help, let me know.

---

### Post by Valkyr333 on 2011-04-07
Hi again,

Sorry for the delay. I've been entertaining a guest and couldn't put enough focus on the task at hand to try and do anything until they had left. I read Problem #2, Solution #1, which states,

"... The fix is to boot an Ubuntu LiveCD/USB, loop mount the wubi root.disk and manually edit the grub.cfg file."

I have an Ubuntu Live CD, but I'm unaware as to how to loop-mount the wubi root.disk, or what changes would need to be made in manually editing the grub.cfg file. Before I boot from the disk and get started, how do I go about doing this?

---

### Post by Rubi1200 on 2011-04-07
If you read a little bit further down you will find all the relevant instructions.

If you would rather we take a look at the setup first, then please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Valkyr333 on 2011-04-07
Okay, for some reason my i386 LiveCD isn't being recognized by the laptop in question. It's not giving me the options menu when I boot-up. I might have burned the image incorrectly or something. I might just end up uninstalling wubi and doing a true partition-install the way I was meaning to originally. I guess the question becomes, assuming I had a proper LiveCD, would installing it with the disc-image I can find at,

[http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease](http://www.ubuntu.com/desktop/get-ubuntu/download#currentrelease)

have me running into the same problem with GRUB?

---

### Post by Rubi1200 on 2011-04-08
If you plan on a proper dual-boot, I recommend 10.04 since it is an LTS (Long Term Support) release.

These are the steps you can take to ensure, I hope, a successful install and dual-boot experience:

1. download the Ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

2. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

4. try as a LiveCD first to see that everything works as it should (don't forget to set BIOS to boot from the CD drive first)

5. from the LiveCD, go to Applications > Accessories > Terminal and post the output of the following command so we can check the state of your drive to make sure there is enough space etc. to do what you want

```
sudo parted -l
```

(lowercase L not 1)

6. backup all important data

7. install

With all this done, you should be ready for a safe and happy dual-booting experience.

By the way, the best site I know of for instructions on how to set up a dual-boot can be found here:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Valkyr333 on 2011-04-08
Thanks for the advice. I'll be sure and do that if I'm sure it would be easier on me to just reinstall it.

This does raise a question about the term LTS, though. I know it means Long-Term Support, and what that means is pretty self-explanatory. However, I'm wondering if that means that therefore there are other Ubuntu versions which aren't chosen to be supported on a long-term basis? For instance, do Maverick, Gutsy, Natty, etc. get less overall attention from the Ubuntu team? If so, what decides this? I imagine it would either be popularity or ease of maintenance, but it can't hurt to ask.

---

### Post by Rubi1200 on 2011-04-08
All releases receive the same security and general updates.

Wikipedia explains the release schedule better than I could:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by Valkyr333 on 2011-04-08
Well then what exactly sets apart an LTS release?

---

### Post by SeijiSensei on 2011-04-08
LTS releases are supported for much longer periods, but their features and bundled software are frozen at the release date.  Security updates and the like are released as needed, but you won't see, for instance, entire new desktop environments like Unity or major DE upgrades like KDE 4.2 -> 4.6.

The support periods are somewhere on the [Ubuntu site](http://www.ubuntu.com/).  

LTS releases are especially valuable for commercial users who want to know that their current deployment will remain stable for a long time into the future.

---

