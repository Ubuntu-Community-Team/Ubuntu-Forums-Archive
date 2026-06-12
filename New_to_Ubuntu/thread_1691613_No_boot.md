---
title: "No boot"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by mark1960 on 2011-02-20
I have an Acer travel mate 2400 which i tried to install ubuto 10.04 all went well - front screen ok various set up questions - i decided to opt for a new total clean instalation as windows xp was installed on another partion - used cd burner xp to create iso image / not just burnt all was hunky dorry - all i have now is a command line which does flash in the top left hand corner but does not respond to any typed command other than ctrl / alt / del which reboots and does a memory check it does offer the f12 option wich does not work with the disc in or out. In desperation I even tried to load win xp again without any luck.
 
system 
intel celron M
512 ram
1.50GHz
40gb
integrated graphics
 
I have checked the comprehensive threads without much luck - can someone please point me in the right direction - Thank you
 
Mark

---

### Post by Rubi1200 on 2011-02-20
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mark1960 on 2011-02-20
Thank you.
 
However,
 
Re: there is no option - 
 
"Try Ubuntu without any changes." 
 
Just the command blink in the top left hand side of the screen.
 
Thank you 
mark

---

### Post by Rubi1200 on 2011-02-20
You need to boot from the CD. First set BIOS to enable booting from the CD-ROM drive and then put the Ubuntu CD in and try again.

Or am I missing something here? Are you able to change settings in BIOS?

---

### Post by mark1960 on 2011-02-20
you are correct i cant acess anything (bios) - just my blank screen no F2 / f12
no nothing.
the only thing other command than the ON button is the Ctrl / Alt /Delete (reboot) are seemingly the only options open to me ?
 
thank you 
mark

---

### Post by hansolo4949 on 2011-02-20
Do you get a screen before the blinking cursor? Also, when the pc is booting, right after you pressed the on button, try pressing esc, or one of the F keys, because those are the usual keys to press to get jnto the bios.

---

### Post by mark1960 on 2011-02-20
Than you.
 
I get Inslyde EFL 50 BIOS V2 10 - if i press the ESC / F button it just skips the memory check.
 
Otherwise no joy.
 
mark

---

### Post by Hedgehog1 on 2011-02-20
> **mark1960 said:**
> I have an Acer travel mate 2400 which i tried to install ubuto 10.04 all went well - front screen ok various set up questions - i decided to opt for a new total clean instalation as windows xp was installed on another partion - used cd burner xp to create iso image / not just burnt all was hunky dorry - all i have now is a command line which does flash in the top left hand corner but does not respond to any typed command other than ctrl / alt / del which reboots and does a memory check it does offer the f12 option wich does not work with the disc in or out. In desperation I even tried to load win xp again without any luck.
 
system 
intel celron M
512 ram
1.50GHz
40gb
integrated graphics
 
I have checked the comprehensive threads without much luck - can someone please point me in the right direction - Thank you
 
Mark

Mark,

We have been observing that a number of laptop computer video drivers seem to work fine during the 'try Ubuntu', but after an installation with all the updates (including updated video drivers) a fair number of folks end up in much the same situation you are experiencing.

The best solution I have at this time is to do a complete re-install - but don't allow any updates either during the install or after the install (the MP3 ones are OK to allow).

Then you need to manually only allow non-video-driver updates once Ubuntu is (we hope) running on your system.

According to the on-line documentation for your laptop, you must press <F2> during post (while the notebook logo is being displayed) to change your boot order.  The documentation did not show the Bios Menus, so you will have to wing that part of it.

Please place the Ubuntu CD back into the CD drive, reboot and press <F2> during post.  Find the boot order, alter it to boot of the CD first, and repeat the install and make sure the 'get updates during install' check box is **not checked**.

Then reinstall Ubuntu - overwriting the previous Ubuntu install.

After installing it will reboot and offer to run about 270 updates - for now, don't let it do that.  This should get you into the basic OS with the GUI running.

Then lets talk about turning off the automatic update check, and instead manually running it - skipping video driver updates.

:KS

---

### Post by Hedgehog1 on 2011-02-20
A less painful way to (possibly) do the same thing:

Press <shift> during a reboot (without the CD installed) to see the GRUB menu.

Arrow down and select Ubuntu with (recovery mode), and press enter/return.

Once the menu comes up (after lots of text scrolls by) arrow down to the 'failsafeX' (Run in failsafe/graphic mode) and hit enter/return.

You will then get options to run in low graphics mode for one session, or to reconfigure graphics.

Select Reconfigure your graphics, click [OK].

Select the default (Generic) configuration, click [OK].

This may get you running without a re-install.

:KS

---

### Post by GlennW on 2011-02-21
I hope this is the right thread. 

I can't boot from a live usb (created with Startup Disk Creator - 10.10) that I have loaded with mint 10 (Julia). There are several options when downloading the iso from KDE DVD to OEM CD (both 32 and 64 bit). I've tried most of them already with no luck. 

I'm wanting to overwrite Ubuntu 10.04 on my Dell Inspiron 6000 with Mint 10 since it requires fewer resources. Upon restart, a line comes up with this:
```
vesamenu.c32: not a COM32R image
boot:
```
It just repeats itself after 10 seconds.

Does anyone have any suggestions? I'm using a Verbatim 8.0 GB usb.

---

### Post by hansolo4949 on 2011-02-21
> **GlennW said:**
> I hope this is the right thread. 

I can't boot from a live usb (created with Startup Disk Creator - 10.10) that I have loaded with mint 10 (Julia). There are several options when downloading the iso from KDE DVD to OEM CD (both 32 and 64 bit). I've tried most of them already with no luck. 

I'm wanting to overwrite Ubuntu 10.04 on my Dell Inspiron 6000 with Mint 10 since it requires fewer resources. Upon restart, a line comes up with this:
```
vesamenu.c32: not a COM32R image
boot:
```
It just repeats itself after 10 seconds.

Does anyone have any suggestions? I'm using a Verbatim 8.0 GB usb.


Glenn, I know you need help, but please do not hijack threads. If you need help, please create your own thread, by clicking the create thread button in the appropriate area if the forums:). I would try using an older Ubuntu image for the live USB. Sometimes you just get a bad ISO, and things go haywire.

---

### Post by hansolo4949 on 2011-02-21
Yes, I concur. You need to reinstall Ubuntu on your computer, and NOT update it. As the old adage says: if it ain't broke, don't fix it :).

---

### Post by GlennW on 2011-02-21
> **hansolo4949 said:**
> Yes, I concur. You need to reinstall Ubuntu on your computer, and NOT update it. As the old adage says: if it ain't broke, don't fix it :).

I didn't mean to hijack the thread. My apologies. However, I want to install Mint 10 over Ubuntu 10.04 on my laptop. That would be reinstalling and not updating.

Thanks for the advise. I'll repost a new thread.

---

### Post by mark1960 on 2011-02-25
Thank you for your reply.

There is no start up screen as such - just a memory check sequence with the option to skip via f12.

If its helps i can utube the very short process - so you can see the actual screen.

I have tried both option as suggested above with no change

It seems that my little travelmate is in lock down?

Here is a link which may explain in more detail

[http://www.youtube.com/watch?v=5PI0fCgb7WU]("http://www.youtube.com/watch?v=5PI0fCgb7WU")

Its all i get with seemingly not a lot to work with?

thank you

---

### Post by mark1960 on 2011-02-25
If the link in the above link is faulty please try this one

[http://www.youtube.com/watch?v=5PI0fCgb7WU&feature=player_profilepage]("http://www.youtube.com/watch?v=5PI0fCgb7WU&feature=player_profilepage")

thank you

---

### Post by mark1960 on 2011-02-27
Has anyone seen the short video? If so any thoughts please?

regards Mark :confused:

---

