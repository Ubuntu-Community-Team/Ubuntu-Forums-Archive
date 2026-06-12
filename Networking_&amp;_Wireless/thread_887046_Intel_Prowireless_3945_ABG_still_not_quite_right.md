---
title: "Intel Pro/wireless 3945 ABG still not quite right"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by new2ubun2linux on 2008-08-11
Hi everyone,

I am still having problems on my Sony Vaio SZ1 with the Intel Pro/wireless 3945ABG card.

After a vanilla installation of Hardy (v8.04.1) the wireless appeared not to work if the wifi switch was off when I boot. The indicator light was off and no networks detected (even if I subsequently turned the switch on - obviously!). If I ensured that the WiFi switch was on on boot it would work OK but with no light. I could even turn it off and on once booted and it would reconnect and work fine.

Installing the linux-backports-modules-hardy-generic module as suggested by chili555 in [http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516) has fixed the light OK (though not sure why as the description in Synoptic packet manager is an "empty package"!!) but it still does not work unless I have the wifi switch on when I boot.

Does anyone (chili555 are you out there?) know if I should try the other bit of advice about the code:

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot

Is that likely to fix this problem/

And if so can you tell me *exactly* how I'm supposed to do that as I am a relative newbie. I assume this is something to run in Terminal. If so, do I 'run' (ie press return) each line separately or what? Is this a one off thing or am I likely to have to do this everytime if I forget to turn on the wifi before booting. Does the reboot line reboot the system for me?

Sorry to be a bit simple, but I'm new to Linux and it's all a bit of a mystery to me! I can work with it as it is and don't want to mess it up if it's unlikely to fix my problem.

---

### Post by chili555 on 2008-08-11
I am indeed out there somewhere! The issue of re-initiating wireless with the switch, or from suspend-hibernate is quite problematic still in Linux; Ubuntu is no exception. I was playing with my switch today (naughty, I know) and no combination of terminal commands could revive my wireless! Only a reboot would work for me. Therefor, I always boot up with the switch in the 'On' position. If I need to save power, I save my no wireless work for last, since I know I'll never get it back until reboot.> not sure why as the description in Synoptic packet manager is an "empty package"Quite a few packages are appended '-generic' and are empty packages whose only purposes are to pull in the real version, for your running kernel, and to pull in updates when you get an updated kernel. If you installed the kernel-specific version of *backports*, then when a new kernel came out, the fixes in *backports* would no longer work.

I doubt very much that the commands having to do with *disable_hw_scan* will do anything to fix the switch behavior. They are two different things entirely. 

If you were to run these commands, you would type, or better, copy and paste in the terminal the first one:```
sudo su
```and press enter. You would be prompted for your password. After entering it, type or copy and paste:```
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```Press enter. Then do:```
reboot
```Your machine would then reboot and the iwl3945 module would be loaded with a parameter disabling hardware scan.

WARNING! If your card is working well now, you do not need to do this. Please do not take chances with commands that don't fix your issue. You could actually make things worse! I only explained it to help you understand how terminal commands work.

---

### Post by new2ubun2linux on 2008-08-12
Thanks chili555, great info, will give you a vote of thanks for getting back and explaining in detail for me. Nice to hear someone who knows what they are talking about.

If I were to try the 'no hardware scan' command, is there a command to reverse the change if it doesn't work? I suppose it would be the same but with '...enable.....' instead of '....disable....'???

Strange thing is that it worked perfectly in Gutsy (v7.10). I could boot with the switch off or on, and the indicator light used to flash as data was transfered which I quite liked. In Hardy and windows it just stays on whenever the card is on. The only thing I found in 7.10 was that all wireless networks showed full strength (on the oringey/brown bar) no matter how weak the signal, but with this driver the strength indicator works fine.

Was the old driver the ipw3945 driver? Was that a restricted driver or something do you know? I seem to remember there was one restricted driver on my system previously.

If your trick with the no hardware scan doesn't work I guess I'll just have to live with it and hope someone fixes he driver soon.

This driver seems like a backward step to me. Don't suppose it is worth revering to the ipw driver?

---

### Post by chili555 on 2008-08-12
> If I were to try the 'no hardware scan' command, is there a command to reverse the change if it doesn't work? I suppose it would be the same but with '...enable.....' instead of '....disable....'???
You can try it temporarily with:```
sudo rmmod iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Test your system and if it's improved, run the permanent commands above. In the unlikely event you decided, after the permanent commands, that is really wasn't working, then:```
sudo rm /etc/modprobe.d/iwl3945
sudo rmmod iwl3945
sudo modprobe iwl3945
```Type and proofread carefully whenever you execute commands; some have the ability to do serious damage. If done incorrectly, of course, they won't have the intended effect, which is fix, or at least improve your system.> Was the old driver the ipw3945 driver? Yes.> Was that a restricted driverNo, as far as I am aware.> Don't suppose it is worth revering to the ipw driver?Ouch! You send shivers down my spine. It's a major undertaking and, in my opinion, a major step backwards. You really want to stuff an '88 Buick motor into your '08 BMW 7-series???> I guess I'll just have to live with it and hope someone fixes he driver soon.That makes two of us. By far, the best solution.

---

### Post by new2ubun2linux on 2008-08-14
Thanks once again Chili555. One more question:

> **chili555 said:**
> You can try it temporarily

does this 'temporary' instruction stay active through a reboot, as the only problem I have is that the wlan has to be switched on during boot, so if the instruction is only for that session it won't help after a reboot.

I will experiment anyway, but thought it might be worth clarifying this for others to see.

PS - sorry about the time between replies, but work keeps getting in the way!

---

### Post by chili555 on 2008-08-14
> does this 'temporary' instruction stay active through a rebootNo. Also, you can remove it immediately with:```
sudo rmmod iwl3945
sudo modprobe iwl3945
```What you will have done is remove the module with its hwscan parameter and reinserted it without. For the intellectually curious, especially those who think they are immune from migraine headaches, please see:```
modinfo iwl3945
```> work keeps getting in the way!I hate when that happens; work, that is!

---

### Post by new2ubun2linux on 2008-08-14
OK, I think I am starting to understand (on a VERY superficial level!) what I am about to try. I'll spend a few mins playing and see if anything works and post back.

Give me half an hour or so...

---

### Post by new2ubun2linux on 2008-08-14
So...

After playing about with it this is what I have found.

1st tried the suggested 'temporary' using:

Code:

sudo rmmod iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

and that seemed to spring the wireless back into action :)

So then I tried the full thing:

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot

But it didn't work after a reboot :(

I therefore applied the reverse, as you said:


Code:

sudo rm /etc/modprobe.d/iwl3945
sudo rmmod iwl3945
sudo modprobe iwl3945

but I have discovered that all I actually need to do is run:

Code:

sudo rmmod iwl3945
sudo modprobe iwl3945

in terminal and that kicks my wireless back to life!:popcorn:

So it seems that all my laptop needs is for the iwl3945 module to be reloaded if the wireless has been switched of (or booted with the switch off) and it jumps into life. I guess the iwl3945 module simply doesn't detect the switch being moved to on.

I suppose I could call this solved for now. Chili555 do you know if there is a quick way to run the above commands without needing to type them into terminal each time?

Thanks for the awesome advice.

---

### Post by dwnokc on 2008-11-03
Thank you Chili555!

---

