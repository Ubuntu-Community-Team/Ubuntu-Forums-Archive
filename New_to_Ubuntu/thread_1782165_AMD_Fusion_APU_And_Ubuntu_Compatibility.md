---
title: "AMD Fusion APU And Ubuntu Compatibility"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Stinky Stinky on 2011-06-14
Hi there everybody! :popcorn:
This is my 1st post :P

I hope you guys go easy on me I am still a newbie lol :(

To cut a long story short I would like to buy an HP 635 because it looks like really good value for money.

However I am very concerned about Ubuntu and it's compatibility with the new AMD E-350 Fusion (Zacate) CPU / GPU or what AMD manufacturers call a APU (Accelerated Processing Unit)

I think it is very new,

Here are some details for those interested:

[http://www.anandtech.com/show/4023/the-brazos-performance-preview-amd-e350-benchmarked](http://www.anandtech.com/show/4023/the-brazos-performance-preview-amd-e350-benchmarked)

And the HP 635 Laptop:

[http://h10010.www1.hp.com/wwpc/za/en/sm/WF06a/321957-321957-64295-3955548-3955548-5086719.html](http://h10010.www1.hp.com/wwpc/za/en/sm/WF06a/321957-321957-64295-3955548-3955548-5086719.html)

Basically is Ubuntu 11.04 (and / or others) compatible with the new AMD Fusion APU?
Will Ubuntu work with the Fusion APU?

I am not too sure I want to purchase something that is not compatible with Ubuntu. I like Ubuntu quite a bit.

Thank you to anyone who can help me! :KS

Thanx

Keep well

Stinky

---

### Post by Vaphell on 2011-06-14
Yes, fusion appears to be nifty, i plan to buy some zacate e350 netbook soon.
From what i have read fusion is generally working, but you may need to get your hands dirty, as gfx drivers are quite fresh and haven't made their way into the official repos yet so manual installation of catalyst and/or adding 3rd party repos is required.
Look for more info using google or ubuntuforums search functions.

I expect that in 11.10 everything will work out of the box.

---

### Post by Stinky Stinky on 2011-06-15
> **Vaphell said:**
> Yes, fusion appears to be nifty, i plan to buy some zacate e350 netbook soon.
From what i have read fusion is generally working, but you may need to get your hands dirty, as gfx drivers are quite fresh and haven't made their way into the official repos yet so manual installation of catalyst and/or adding 3rd party repos is required.
Look for more info using google or ubuntuforums search functions.

I expect that in 11.10 everything will work out of the box.

Hey thanx Vaphell ;)

That is basically the info I needed.

So it seems I will need to do a little work, that shouldn't be too hard I guess.

Hopefully it will work all right when version 11.10 comes out.
But most things should work when I 1st install.

Thanx!

Stinky

---

### Post by lukeskope on 2011-06-15
Hi, i felt compelled to reply because i just got an Acer laptop with the AMD E-350 chip and have done a bunch of testing.

I've installed Ubuntu 11.04 with Unity, Linux Mint with Gnome and Fedora 15.  With Ubuntu and Mint (which is now, after all my tweaking, just a Minty Ubuntu 11 with Gnome instead of Unity).  I am up to the 3.0 Kernel with a fully updated display driver stack.

In all cases the proprietary driver from Catalyst works better, performance is overall faster, effects work better and video playback is smoother.  But, you can't put the laptop to sleep.  This is a known bug and it is not clear when it will be fixed.

The open source drivers do work ok, though I haven't tried any 3d stuff.  Video on the internet, Hulu, Youtube, play ok, sbut not stellar, compared to the Catalyst driver (and also compared to the Win 7 install I have on another partition on the same laptop). I actually boot into Windows to watch Hulu.

If Catalyst fixes the sleep bug or the opensource drivers get better Linux is a great OS for this chip, but it's still a little new, and has some rough edges.

---

### Post by prebbish on 2011-06-18
Hi!

Have any of you guys tried installing XBMC? 

Im interested in knowing because i'm planning to buy an Asus board with the AMD e350 for an HTPC running XBMC on linux/ubuntu.

---

### Post by Eugenian on 2011-06-21
> **Vaphell said:**
> Yes, fusion appears to be nifty, i plan to buy some zacate e350 netbook soon...

The E-450 is just around the corner:

[http://www.anandtech.com/show/4407/the-brazos-update-amds-e450](http://www.anandtech.com/show/4407/the-brazos-update-amds-e450)

---

### Post by spych102 on 2011-07-17
I have a Sony laptop with an e350 chip and it freezes after about 15 minutes with the Wubi default 64 bit Ubuntu 11.04 whether unity or 3d effects are turned on or off, I have to say that it is absolutely shockingly bad. As soon as I switched to 32 bit Ubuntu it works without crashing. It's a crying shame that I can't use the CPU to its full potential.

The graphics drivers are pretty bad - I get screen tearing with both the opensource drivers and the catalyst drivers. The catalyst drivers actually cause garbled artifacts in the Unity sidebar.

Actually the graphics are very nice in Windows 7. If I were anything other than an Ubuntu diehard I'd be switching to the dark side...

---

### Post by naticus on 2011-07-29
> **spych102 said:**
> I have a Sony laptop with an e350 chip and it freezes after about 15 minutes with the Wubi default 64 bit Ubuntu 11.04 whether unity or 3d effects are turned on or off, I have to say that it is absolutely shockingly bad. As soon as I switched to 32 bit Ubuntu it works without crashing. It's a crying shame that I can't use the CPU to its full potential.

The graphics drivers are pretty bad - I get screen tearing with both the opensource drivers and the catalyst drivers. The catalyst drivers actually cause garbled artifacts in the Unity sidebar.

Actually the graphics are very nice in Windows 7. If I were anything other than an Ubuntu diehard I'd be switching to the dark side...

Exactly the same here but with c-50 + radeon 6250.  Screen tearing in both Opensource drivers and Catalyst.  Really hoping that some good drivers come out soon for Fusion, because it seems so perfect for Linux.

If anyone has any tips I am all ears.

*BTW the opensource drivers work better on my Aspire one 722 than the proprietary AMD versions.

---

### Post by janusman on 2011-08-30
This is my first post in the forums =)

I just got a Lenovo All-In-One C205 which has the E-350 and ATI Radeon 6310 gfx. However, I have not gotten it to display properly *at all*... booting the live CD using the nomodeset flag does boot up (I can hear the ubuntu sound) but the screen progressively (but quickly) gets turned from full black into what seems a whiteish garbled version of the Ubuntu logo... so I'm going to try updating the Kernel tonight from what comes on the standard Natty CD and see if that helps.

---

### Post by janusman on 2011-08-31
Yay! I fixed my display problem!

Starting out from the Natty Ubuntu install (using the Text-mode installer from the Alternate install ISO) and booting into text mode (by editing the Grub line and adding "text" at the end), hitting CTRL-ALT-F1, logging in and then using the commandline.

I used some of the steps outlined in [http://forum.xbmc.org/showthread.php?t=106898](http://forum.xbmc.org/showthread.php?t=106898) ...

```
sudo apt-get install -y dkms

cd ~; mkdir catalyst11.7; cd catalyst11.7
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run
chmod +x ati-driver-installer-11-8-x86.x86_64.run
sudo sh ./ati-driver-installer-11-8-x86.x86_64.run --extract ati
cd ati
sudo ./ati-installer.sh 8.881 --buildpkg Ubuntu/natty
cd ..
rm -rf ati
sudo dpkg -i fglrx*.deb

sudo aticonfig --initial -f
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Then, sudo reboot... let the normal boot sequence start and lo an behold, gfx were now working (at least, Unity does!) =)

The GUI feels a little slow, and I've yet to see how the CPU scaling is set... but at least the system appears usable now =)

---

### Post by nej_simon on 2011-09-05
Hello!

I got a Samsung 305U1A yesterday that's based on the e350 APU. Everything works in 11.04 (64 bit)except two things:

The fglrx driver doesn't work properly. It causes the kernel to output a bunch of ACPI-errors in dmesg and breaks suspend. The desktop also becomes a bit laggy when the driver is active. The open source driver works though. The latest driver from AMD has the same issue.

The screen has bacome garbled with horizontal lines at two occasions, once when I left the computer for a while compiling a kernel and once after resuming from hibernation. This is with the open source radeon driver, I don't use fglrx due to the other problem. I'm not sure what to do about this.

I also had to install a updated psmouse driver to get the touchpad to work properly:
[http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2](http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2)

---

### Post by Kuzma86 on 2011-09-07
I got myself a Zbox with E-350 for the living room PC. Everything works out of the box on the 11.04 including HDMI sound, which used to be a problem before. 

Unfortunately I can't watch 720p youtube videos and high quality video files. The picture staggers considerably and I can't really understand why. The graphics should in theory be able to handle 1080p just fine and adding more RAM hasn't helped.

Any thoughts?

So far I was thinking of waiting for 11.10 and if that doesn't help trying Mint. But should Mint improve high res playback? I am not so sure!

---

### Post by snip3r8 on 2011-09-07
> **Kuzma86 said:**
> I got myself a Zbox with E-350 for the living room PC. Everything works out of the box on the 11.04 including HDMI sound, which used to be a problem before. 

Unfortunately I can't watch 720p youtube videos and high quality video files. The picture staggers considerably and I can't really understand why. The graphics should in theory be able to handle 1080p just fine and adding more RAM hasn't helped.

Any thoughts?

So far I was thinking of waiting for 11.10 and if that doesn't help trying Mint. But should Mint improve high res playback? I am not so sure!
I would say your video playback is a graphics driver problem,11.10 is the better way to go,you could even try the 11.10 beta if you are eager

---

### Post by sunRAHH on 2011-09-23
I just got the HP 635 with AMD Fusion chip. Everything seems to work under 11.04 and pretty stable although it is very sluggish. Running demanding programs like word 2007 and photoshop under wine can be slow. some photoshop plugins almost unusable, even with 4gigs RAM.

tried ubuntu 11.10 but too many forced closures

it's a nice machine and very good value but now I would have gone for one of the higher performance processors – fusion is too slow :-)

anyone tried 64 bit yet?

---

### Post by JayKay3OOO on 2011-10-04
I tried this out on 11.04 and SD and HD flash were complete fail, the extra graphics driver helps a bit, but the catalyst option to prevent tearing seems to chew cpu cycles. Turn this off and the video speeds up a bit, but tearing occurs with some lag still present.

If you watch a lot of internet tv then on 11.04 it's not going to work out for you.

Loving it in windows though! HD and SD video is fine and the chip, while not stellar uses so little power I almost forget I have the unit sitting on my desk because it's so quiet.

Bios boot is fast as a laptop and I can't actually tell that much difference in speed from my 3.6GHZ phenom 2 x4 965be when loading the OS, except that my hyper X ddr3 1600 is limited to 1333 and single channel!

Well worth getting into if you need a small, low powered machine.

Just don't expect it to do all your video editing tasks... ...fast.

---

### Post by Stinky Stinky on 2011-10-12
Hey guys I found a very interesting article here:

[http://www.phoronix.com/scan.php?page=article&item=amd_fusion_e350&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_fusion_e350&num=1)

But it is very strange because the AMD E-350 Fusion CPU / GPU looks pretty damn capable... on Windows that is...... :(:

[http://www.youtube.com/watch?v=J3Y7b_K5Cvw&feature=related](http://www.youtube.com/watch?v=J3Y7b_K5Cvw&feature=related)

Has any one tried the ATI Catalyst drivers instead of the Open Source drivers???

How does it perform?

What version of Ubuntu (Or other Linux OS ) are you running and with what drivers?

What kind of performance do you get?

Thanks to any body who answers :)

Keep well

Regards

Stinky

---

### Post by prebbish on 2011-10-13
Hi! 

You should check this thread out:

[http://forum.xbmc.org/showthread.php?t=106898&highlight=AMD+E350](http://forum.xbmc.org/showthread.php?t=106898&highlight=AMD+E350)

---

### Post by freedomorfire on 2011-10-15
> **Stinky Stinky said:**
> Hey guys I found a very interesting article here:

[http://www.phoronix.com/scan.php?page=article&item=amd_fusion_e350&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_fusion_e350&num=1)

But it is very strange because the AMD E-350 Fusion CPU / GPU looks pretty damn capable... on Windows that is...... :(:

[http://www.youtube.com/watch?v=J3Y7b_K5Cvw&feature=related](http://www.youtube.com/watch?v=J3Y7b_K5Cvw&feature=related)

Has any one tried the ATI Catalyst drivers instead of the Open Source drivers???

How does it perform?

What version of Ubuntu (Or other Linux OS ) are you running and with what drivers?

What kind of performance do you get?

Thanks to any body who answers :)

Keep well

Regards

Stinky
I'm using the xorg-edgers stuff found [here]("https://launchpad.net/~xorg-edgers/+archive/ppa") and the difference between the stock ones and these is definitely noticeable.

---

### Post by rgm3 on 2012-01-11
> **Kuzma86 said:**
> I got myself a Zbox with E-350 for the living room PC. Everything works out of the box on the 11.04 including HDMI sound, which used to be a problem before. 

Unfortunately I can't watch 720p youtube videos and high quality video files. The picture staggers considerably and I can't really understand why.

I have the same system, and have been struggling.  To answer your question directly: the linux drivers for the graphics part of the E-350 chip suck.  It's been very difficult for me to get hardware-accelerated video playback working with this system.  I'm using Ubuntu 11.10 Oneiric and AMD Catalyst 11.12 released 12/13/2011, and have had no luck at all (even though running the "vainfo" command indicates that things ought to be working).  I briefly had it working well using an older Catalyst release on this system.  I pored over this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

I also tried uninstalling the AMD drivers that I manually downloaded and simply used Ubuntu's built-in restricted drivers wizard (jockey-gtk) but that didn't give me hardware acceleration either, despite "vainfo" claiming otherwise.

I'm going to try falling back to Catalyst 11.10 or 11.11 tonight.

---

### Post by ramboseahorse on 2012-01-30
> **prebbish said:**
> Hi!

Have any of you guys tried installing XBMC? 

Im interested in knowing because i'm planning to buy an Asus board with the AMD e350 for an HTPC running XBMC on linux/ubuntu.

XBMC runs great on my e-350 laptop, running Ubuntu 11.04 with the Catalyst Drivers. I haven't had any problems installing plug-ins. Video playback isn't choppy and I can also stream to other XBMC devices with no problems.

---

### Post by prebbish on 2012-01-30
> **ramboseahorse said:**
> XBMC runs great on my e-350 laptop, running Ubuntu 11.04 with the Catalyst Drivers. I haven't had any problems installing plug-ins. Video playback isn't choppy and I can also stream to other XBMC devices with no problems.

Since this thread was created I have bought a E-450 setup, and I agree. Video playback is no problem, but getting hardware acceleration working with flash was next to impossible for me (Need it to watch American Football via NFL Gamepass). 

So instead I installed Win 7, and this has actually caused some problems with streaming video from my NAS, sometimes the video stutter a bit, but in 720p it is watchable, but not perfect. So when the NFL season ends this sunday (Go Pats!) I will install Ubuntu again and work some more with the flash problem :P

---

### Post by Linuxisfast on 2012-02-07
Using latest Catalyst 12.1 installed manually on my 1015-B netbook. It runs fine, movies work well with vlc installed via muench ppa where GPU is enabled. HDMI movies run with 20% peak CPU usage.

---

### Post by Linuxisfast on 2012-02-18
On all AMD Fusion, here is my recommendation based on my experience with the ASUS 1015-B C50 powered netbook. Install latest Catalyst from their website and not via hardware drivers as xwat ppa has older version of the driver. If you follow [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) then install goes very smoothly. Make sure xvba-va driver is installed and then install latest vlc from muench/vlc ppa [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc) Enable GPU acceleration under VLC>input and codecs and you will have full HDMI performance like I do on my C50 Netbook.

---

### Post by leopoldbirkholm on 2012-04-08
Very interesting thread.

I have two computer with the APU. One MSI X370 running AMD APU E-350 and an Acer eMachines running AMD APU E-300. Not one of this will run Ubuntu. One I got Fedora to boot but then the WiFi would not work so that was a bust. The WiFi (Realtek RTC8188CE) was after some digging a low supported card for Linux.

I am awaiting 12.04 LTS and see if that might solve my problem.

My adding would be the question if anyone else has experience issue with using the AMD platform instead of Intel? Past or present?

//Leopold

---

### Post by kaldor on 2012-04-08
> **leopoldbirkholm said:**
> Very interesting thread.

I have two computer with the APU. One MSI X370 running AMD APU E-350 and an Acer eMachines running AMD APU E-300. Not one of this will run Ubuntu. One I got Fedora to boot but then the WiFi would not work so that was a bust. The WiFi (Realtek RTC8188CE) was after some digging a low supported card for Linux.

I am awaiting 12.04 LTS and see if that might solve my problem.

My adding would be the question if anyone else has experience issue with using the AMD platform instead of Intel? Past or present?

//Leopold

God morgon!

I recommend you give 12.04 a try on a live USB session. It should give you an idea as to how well the APU will work. You can also drop by #U+1 on IRC (irc.ubuntu.com) to see if anyone else has experience with it.

---

### Post by leopoldbirkholm on 2012-04-10
[quote=kaldor] It should give you an idea as to how well the APU will work. You can also drop by #U+1 on IRC (irc.ubuntu.com) to see if anyone else has experience with it.[/quote]

Yes, I will try it. I have manged to download the AMD64 version, IE Ubuntu 12.04 LTS Unity Beta for AMD with the 64-bit archicture (how do one spell it?).

I will try the IRC. Right now, I just get a blank image when trying your link. =/

---

### Post by Dlambert on 2012-04-10
Probably need the AMD drivers though...

---

### Post by leopoldbirkholm on 2012-04-10
I am now running Ubuntu 12.04 LTS Beta on my eMachines E443 with an APU from AMD named E300 Dual-Core. It works overall fine, except that the update manger don't work.

Yeh, hibernate don't work either. Forgot that.

---

