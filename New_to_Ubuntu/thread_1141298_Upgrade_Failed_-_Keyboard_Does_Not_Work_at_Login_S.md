---
title: "Upgrade Failed - Keyboard Does Not Work at Login Screen"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by parkavenue on 2009-04-28
I’m a bit of a linux newbie – my dell laptop boots to 8.04 and I use VirtualBox to run WinXP for a game. I was upgrading from 8.04 to 8.10. I left for about 6 hours and when I came back to my computer it seemed that there wasn’t an upgrade going on anymore and there weren’t any windows open. (I don’t quite remember, but I believe the Update Manager was open but not doing anything.) So I selected “Close” and restarted my computer. Now apparently whenever I get to the login screen my keyboard does not work (although it works before that so I can get into the bios settings). 
Any ideas on how to fix this? 

My keyboard works when I boot from the live CD so I could pull all my files off and do a fresh install but I would rather not. Or perhaps someone knows of a file that I need to edit to fix the problem?

Also, I didn’t think of checking my partition once running the live CD but I believe the upgrade failed for some reason and I’m still running 8.04.

Thanks in advance.
-parkavenue

---

### Post by Kareeser on 2009-04-28
Odd. Switch between a hard reset and a soft reset, and see if you get keyboard control back...

---

### Post by parkavenue on 2009-04-28
Thanks for the reply! I'll have to try that tonight after work. (I knew should have brought the laptop with me today!)

Also, not sure if this will be a clue but I plugged in a USB keyboard and still couldn't log in (although again, I could get to the bios).

---

### Post by parkavenue on 2009-04-28
Alternating a hard then soft reset did not solve the problem... 

Any other ideas? Keyboard works until I get to the login screen. Caps lock/num lock still toggle but no keys show up in the username field.

I'll keep checking in...

---

### Post by Kareeser on 2009-04-28
Really, so the keyboard works, but nothing actually appears?

Try changing keyboard settings... I think you can do that from the login screen using the mouse.

---

### Post by parkavenue on 2009-04-28
I can choose Options in the lower left hand corner. From here I get: Select Language, Select Session, Remote Login via XDMCP, Restart, Shut Down, Suspend, Hibernate.

Remote Login via XDMCP brings me to another GUI login-type screen but I can't type there either.

Under Select Session: Last Session, Run Xclient script, GNOME, Secure Remote connection, Failsafe GNOME, Failsafe Terminal. I didn't really try all of these but I think a few of them just kept me at the main login.

When I hover over the username it says "Answer questions here and press Enter when done. For a menu press F10." but I obviously can't press F10.

---

### Post by Didius Falco on 2009-04-28
> **parkavenue said:**
> Alternating a hard then soft reset did not solve the problem... 

Any other ideas? Keyboard works until I get to the login screen. Caps lock/num lock still toggle but no keys show up in the username field.

I'll keep checking in...

I found this while doing a search, so I have no clue if it will work for you or not. It did work for several other, but they are all using Lenovo 3000 Y500 laptops, though. But, when I found it, my search terms included Lenovo, so... I'm wondering if it's a laptop specific problem.

Please post back the results, so I'll know if it works, in case the question comes up again.

You need to edit your menu.lst file. You can do this from within Ubuntu using a Terminal shell. The first thing to do is backup the menu.lst file, so you have a copy to restore if needed. In the Terminal window, type ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```Then type ```
gksudo gedit  /boot/grub/menu.lst 
```In the menu.lst file, you'll see a list of kernels, something like this:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```You want to add "i8042.reset" to the end of the kernel line, so the above would like like this:

```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```Try with just the top entry, the one you normally boot into. Save the file and reboot. Try it out for a while, reboot a few times and see if it makes a difference.

If it fixes it, remember to go back into the menu.lst file and add it to the end of all the other "kernel" lines.

Also, remember to edit your menu.lst every time you get a kernel update and add it to the new kernel lines.

I hope this fixes the problem - it's worth a shot, at any rate. If it doesn't, you can just edit the "i8042.reset" out of your menu.lst file and be back to where you are now.  Please post back and let us know.

---

### Post by parkavenue on 2009-04-28
I put the i8042.reset in the menu.lst but I didn't see any change. (I'll go in and remove it later.)

I tried Ctrol-Alt-F1 to get to the command line and I can actually type, and I can log in from there, but now what? I told you I was a newbie but can I get into the desktop from here? I typed sudo reboot and that rebooted but I didn't know what else to try...

Kareeser and Didiu, thanks again for your assistance! I hope we're getting somewhere! [-o<

---

### Post by Kareeser on 2009-04-28
This is extremely rare, as usually, keyboard control completely locks up, including ctrl-alt-f1, etc.

Here's a thought... did you try another keyboard? The simplest solution may be to just swap out that keyboard for another.

---

### Post by parkavenue on 2009-04-28
I should have mentioned this in the first post but it's a Dell laptop. And I did try a USB keyboard but got the same results. I actually have no problem typing from the command line or from a live CD using the laptops keys.

So I'm just hoping there is a way that I could get to the desktop from the command line, even if it was a work-around that I had to do each time, for now. I'd like to re-try the upgrade to 8.10 (and eventually 9.04). Otherwise, I'll use the CD to pull my data and start fresh. Thanks again.

---

### Post by Didius Falco on 2009-04-28
Note: disregard these steps. I misread your earlier post and thought that you had said you were able to log in from the command line.

------------------------------------------------------------------------------------------
As a temporary workaround, you could just set your pc to automatically log you in.

1. Use the command line technique to log in.

2. Go to your Fast User Switcher and Right Click.

3. Choose Set Up login Screen and enter your password.

4. Go to the Security Tab.

5. Tick the Automatic Login radio button and choose your username from the drop-down list.

It'll log you in automatically from then on.
------------------------------------------------------------------------------------------

On Edit:

Open a Terminal and type ```
lsb_release -a
``` and see what version you have.

---

### Post by parkavenue on 2009-04-28
Sorry if this is obvious but I'm hung up on the command line... When I type Ctrl+Alt+F1, I get the command line (parkavenue@parkavenue-laptop:~$) and type my username and password but I'm left at the command line. How do I get by this to the desktop?

The lsb_release command gives me 8.04.2.

---

### Post by sama_j on 2009-04-28
Try 

> start x

---

### Post by Didius Falco on 2009-04-29
> **parkavenue said:**
> Sorry if this is obvious but I'm hung up on the command line... When I type Ctrl+Alt+F1, I get the command line (parkavenue@parkavenue-laptop:~$) and type my username and password but I'm left at the command line. How do I get by this to the desktop?

The lsb_release command gives me 8.04.2.

Reboot and choose the Recovery Mode line. When you get the list of choices, choose the root shell with network support.

From the command line, issue these three commands, in order:

 
```
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by parkavenue on 2009-04-29
Interesting... I had found a post suggesting "sudo apt-get update" while I was waiting but not "upgrade." I expect "sudo apt-get upgrade" is going to take some time. On my way...

So will the dist-upgrade command be grabbing the latest distro?

Thanks again.

---

### Post by parkavenue on 2009-04-29
> **Didius Falco said:**
> Reboot and choose the Recovery Mode line. When you get the list of choices, choose the root shell with network support.

From the command line, issue these three commands, in order:

 
```
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Success! :P The above code solved it.
I got back to the splash screen after "sudo apt-get upgrade", still had the issue (keyboard could not type in username). So did I Ctrl-Alt-F1 to get back to command line (at this point lsb_release indicated that I was in 8.10). So I typed in the last command "sudo apt-get dist-upgrade". When I got to the splash screen, still no luck. So I rebooted and (finally) when I got to the splash screen, I could log in!
Thanks again to those who helped! Didius, thanks for your most recent suggestion!

---

### Post by parkavenue on 2009-04-29
First off, thanks again to all that helped! Is there a way to mark this thread as solved or do we have get to the root of the problem?

I'm still don't know the actual cause. So here's a recap of what occurred and how it was solved. Hopefully it helps someone in the future:
 1. My laptop apparently failed during the initial upgrade from 8.04 to 8.10.
 2. I did a restart. Upon getting to the splash screen, my keyboard had failed (I could Ctrl-Alt-F1 to the command line but I could not type in my username).
 3. Tried various combos of hard/soft resets without success.
 4. Finally, the following code upgraded me to 8.10 via the command line. This fixed the keyboard problem at the splash screen. NOTE: I got to the splash screen after the 2nd command and it still wasn't working, so I had to Ctrl-Alt-F1 back to the command line to type the third command. When this finished I still couldn't type at the splash screen until I rebooted.

```
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get dist-upgrade 
```

=D>

---

### Post by Didius Falco on 2009-04-29
That's great!! You summed up the fix very well, so others will find this thread useful.

To mark the thread solved, edit your first post. When the edit screen comes up, click the "Go Advanced" button. From that screen you can edit the title of the thread. Click the back end of the title and type in "solved" - partway through typing it you'll get a drop-down list of variations that you can choose from.

Add a solved Tag and save.

Then go enjoy yourself - you've earned it! :guitar:

---

### Post by parkavenue on 2009-04-29
Thanks but I couldn't see what you were describing so I did some searching and it seems that tagging as solved is missing for now (as of 5 days ago?).
[http://ubuntuforums.org/showthread.php?t=1135257](http://ubuntuforums.org/showthread.php?t=1135257)
 
No biggie, I'll just change the thread title without a solved tag.

---

