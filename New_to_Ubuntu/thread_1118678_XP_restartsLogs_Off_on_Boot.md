---
title: "XP restarts/Logs Off on Boot"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by nml on 2009-04-07
Hey All,

I used GParted and changed some partions with a duel boot system last night...specifically, I shrunk my Ubuntu partition, enlarged my XP partition and created a new partition.

I thought it went well and on boot, I go (like before) straight to Ubuntu, but I'm unable to sucessfully boot into XP (I choose it with grub, it boots, then immediately 'logs off' and goes back to the initial log screen)...

Any ideas on how to make the system log back to XP... or do I have to reinstall XP (and remodify my grub loader?)

TIA,

Mick

---

### Post by billgoldberg on 2009-04-07
> **nml said:**
> Hey All,

I used GParted and changed some partions with a duel boot system last night...specifically, I shrunk my Ubuntu partition, enlarged my XP partition and created a new partition.

I thought it went well and on boot, I go (like before) straight to Ubuntu, **but I'm unable to sucessfully boot into XP (I choose it with grub, it boots, then immediately 'logs off' and goes back to the initial log screen)...**

Any ideas on how to make the system log back to XP... or do I have to reinstall XP (and remodify my grub loader?)

TIA,

Mick

Does Windows actually starts booting and then just quits or does it never gets to Windows?

If you want to check your Windows install is still working, download a copy of the "super grub disk" live cd and use that to boot into Windows.

You can use it to restore the Grub if the problem lays there.

---

### Post by nml on 2009-04-07
boot starts, hit escape to go to grub menu...choose XP.  Boot starts, stays dark for a couple of minutes, then screen turns blue and my user name and password field pops up.  I'll enter pw and hit enter, and the system will either log off or shutdown...I can't get into windows.

I'll be happy to dl and run super grub disk, but what am I looking for as far as restoring the Grub?

thanks,

Mick
(heading off to get Super Grub disk)

---

### Post by billgoldberg on 2009-04-07
> **nml said:**
> boot starts, hit escape to go to grub menu...choose XP.  Boot starts, stays dark for a couple of minutes, then screen turns blue and my user name and password field pops up.  I'll enter pw and hit enter, and the system will either log off or shutdown...I can't get into windows.

I'll be happy to dl and run super grub disk, but what am I looking for as far as restoring the Grub?

thanks,

Mick
(heading off to get Super Grub disk)

I suggested the Super Grub disk as I thought you couldn't get into Windows.

There is nothing wrong with the grub.

It boots Windows.

The problem is with Windows, not the grub or Ubuntu.

---

### Post by nml on 2009-04-07
> It boots Windows.

The problem is with Windows, not the grub or Ubuntu.

so, would the solution be to reinstall XP?  If so, should I have the option to install it over the current installation and then resetup the Grub menu.lst?

thanks...

---

### Post by Chilli Bob on 2009-04-07
I think the change of partition size makes XP think it has been put into a different PC.  (This sounds like the exact symptoms I got when I put my existing hard drive into a new PC)

There is a repair mode on the XP installation CD if you have it handy.  This may avoid having to do a re-install, but it will probably screw up GRUB again.

---

### Post by nml on 2009-04-07
Hey Bob,

Do you mean boot from cd, then run the 'automatic recovery mode'?

---

### Post by Paidhima on 2009-04-07
EDIT: Do not run 'automatic recovery mode'.

This is definitely not a Grub issue.  It's Windows.  Specifically, it's usually wsaupdater.exe.  Here's how you fix it (if this is indeed the issue):

1.  Boot to the recovery console.  If you have a WinXP disc, boot to it and it will let you do this.  If not, you may have the option if you use F8 after the BIOS screen to bring up boot options.  If neither of these come up, you may want to look around for a bootable CD online that will get you to the recovery console.  They exist.

2.  At the recovery console, choose your Windows installation (should just be one) and enter the admin password.  If you never set one, try leaving it blank and just hit enter.

3.  Type the following bolded lines (not the unbolded comments), one line at a time and hit enter after each one:

**cd \**
**cd c:\windows\system32**
**copy userinit.exe wsaupdater.exe**
**exit** and restart Windows normally.

You should now be able to log in.  To complete the fix:

4.  Open the registry (START > Run... > regedit)

5.  In the pane at the left, navigate to *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\*

6.  Change *C:\WINDOWS\System32\wsaupdater.exe* to *C:\WINDOWS\System32\userinit.exe*

---

### Post by nml on 2009-04-07
thanks Paidhima...

I tried it and got through the first part exactly as you wrote it...

I entered **exit**, removed the XP cd and waited for the restart..grub loaded and I picked my XP install.  Boot started got to the 'log On to Windows' screen which has my UN and space to enter PW.  Nows where I hang up...(no change since trying your instructions....can't log in)

When I enter my password and hit 'OK', the screen goes black, then it flashes a popup that says 'Loading Your Personal Settings' then goes immediately to the 'logging off' popup then back to the 'Log On to Windows' screen.  My only option then is to do the same thing (hit OK) or to 'Shut Down'..

any other suggestions I can try...

Many thanks...

---

### Post by Paidhima on 2009-04-07
@nml

No problem - we still have some options here.  You're going to need to boot back into the recovery console.  Rather than copy the existing userinit.exe, we're going to replace it with the original from the i386 folder on your WinXP disk.

So:

1.  Boot to recovery console.
2.  Use the following commands:

**D:** - Your optical drive may be something other than D:, so keep that in mind.
**cd i386**
**expand userinit.ex_ c:\windows\system32** - Note that the ex_ is not a typo, and there's a space between .ex_ and c:\blahblah.
**copy userinit.exe wsaupdater.exe**
**exit** and boot to Windows.

See if that helps.

---

### Post by lisati on 2009-04-07
Just wondering: is the OP using XP on a Compaq machine with an AMD64 processor? This is vaguely reminiscent of a problem I experienced a while back, possibly unrelated, after installing XP SP3, which showed up about the same time I had done a fresh install of Ubuntu. and for which there's a patch available at the Compaq website.

EDIT: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-60484-2&lc=en&dlc=en&cc=nz&lang=en&os=228&product=1102915](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-60484-2&lc=en&dlc=en&cc=nz&lang=en&os=228&product=1102915)

---

### Post by nml on 2009-04-07
Paidhima,

You are the man (err, person)..seems to be OK, or at least it looks like I'm up and running again (yep, optical drive was different)... I really appreciate your efforts...and am envious of your knowledge about XP..

thanks again,

Mick
(sure I'll be back with tons of problems)

---

### Post by nml on 2009-04-07
> Just wondering: is the OP using XP on a Compaq machine with an AMD64 processor?

No....using an old IBM laptop....Intel processor

thanks for the thoughts.

---

### Post by Paidhima on 2009-04-07
No problem!  Hopefully it stays fixed, hehe.

---

