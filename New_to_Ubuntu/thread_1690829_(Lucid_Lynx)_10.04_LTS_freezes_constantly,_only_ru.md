---
title: "(Lucid Lynx) 10.04 LTS freezes constantly, only runs stable on failsafeX mode"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by tech_freak on 2011-02-19
Hello friends,
I recently moved on from windows to open source. I fell in love with lucid lynx at the very first use on my brothers laptop. so i decided to use it initially on persistence mode using my transcend 2 GB flash drive with win 7.
1) It did boot up but started to freeze randomly after booting and a hard reboot was the only way for restarting it. 
2)I tried killing X machine using ctrl+del+bcksp but it didnt seem to work. Then i tried alt+print scrn+R,E,I,S,U,B and then ctrl+alt+del. After this it would reboot but then i had to deal with the same problem of random freezes again on persistence as well as live mode.
3)After getting a little disappointed, I switched back to windows 7. Then i installed lucid lynx on a 15 GB partition to dual boot with win 7. It worked fine and there were no problem in installation. It even booted without any problems.:P
4)But the problem of freezes on clean installation was far worse then on persistence or live mode. My system would freeze up after about 1 minute after the login.And again i had no way other than using alt+print scrn+R,E,I,S,U,B as killing X server would not work and neither did the light restart mode work for me.:mad:
5)After wards i went to recovery mode and started running ubuntu through failsafeX mode. It works fine without any problems. But again I miss compiz and beryl which would only be available in normal mode.:(
ANY HELP IN THIS MATTER WILL BE GREATLY APPRECIATED !!!:popcorn:
SPECIFICATIONS=>
- Intel P4
- 1GB DDR2 RAM
- 160GB Hard Drive
- DVDRW
- 17" HD
- Windows 7 Enterprise Edition 32-Bit

---

### Post by fabricator4 on 2011-02-19
What video card are you running?

Try turning off visual affects completely and see if that improves things for you.

Chris

---

### Post by tech_freak on 2011-02-19
Hope this helps.

                description: VGA  compatible controller              product: 82945G/GZ Integrated Graphics Controller              
vendor: Intel  Corporation              physical id: 2
              bus info: pci@0000:00:02.0
              version: 02              
width: 32  
bits              clock: 33MHz              
rom               configuration:  driver=i915  latency=0

and yeah i tried turning the visual effects to none in normal mode but it would still freeze

---

### Post by fabricator4 on 2011-02-19
Googling that video chipset doesn't reveal any real problems since Jaunty.  You might want to do some Google and forum searches to see if there's anything I missed however.

I discounted a problem with the system RAM as you don't have any problems running under recovery mode.  It could be video RAM... do you ever see any junk or messed up graphics on the screen?  I can't remember if memtest86+ will test video RAM, have a look.  

In the absence of any error messages or any other indication of what the problem may be it's a bit hard to know what's going on.  You might have to look at the logs to see if there's any crash reports or something that will give a clue.  Run the machine until it halts and note the system time, then reboot in recovery mode and use the log file viewer under  system/administration to see if there's anything in there.

Is it possible to borrow another video card to try in that system? It doesn't have to be high spec, just something that can be used for testing.

Chris

---

### Post by Dutch70 on 2011-02-19
> **tech_freak said:**
> Hope this helps.

                description: VGA  compatible controller              product: 82945G/GZ Integrated Graphics Controller              
vendor: Intel  Corporation              physical id: 2
              bus info: pci@0000:00:02.0
              version: 02              
width: 32  
bits              clock: 33MHz              
rom               configuration:  driver=i915  latency=0

and yeah i tried turning the visual effects to none in normal mode but it would still freeze

Hahaa...I read your post last night & have been waiting for you to post your video card.
obviously, I have the same card. 

Keep this & pass it around... Post #22, Page 3, is all you need
[*[COLOR="Red"]intel 82945G Desktop Effect Hang[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1307001")

Don't worry that it's Karmic. Just be sure to write down the directions before you go into a tty. It's not near as difficult as it may seem at first. I'm not even sure I understood the part at the bottom, but it worked what seemed to be a miracle on my machine.

Best Regards

---

### Post by tech_freak on 2011-02-20
@[Dutch70]("http://ubuntuforums.org/member.php?u=595401")
WUUHUUUUU, it worked like a charm man, thank you !!!! MY PC FREEZES NO MORE !!!
The fault is I just didnt understand as to why we uninstall compiz and then reinstall the core again?
Is there some problem with the installation of lucid and compiz initially which causes hardware conflicts, or is it just that we are installing new compiz core altogether for video card compatibility.
Anyways I am changing the header to SOLVED...
@[fabricator4]("http://ubuntuforums.org/member.php?u=761043")
thank you for your suggestion too.

HUMANITY TOWARDS ALL !!!!!
Regards.

---

### Post by Dutch70 on 2011-02-20
> **tech_freak said:**
> @[Dutch70]("http://ubuntuforums.org/member.php?u=595401")
WUUHUUUUU, it worked like a charm man, thank you !!!! MY PC FREEZES NO MORE !!!
The fault is I just didnt understand as to why we uninstall compiz and then reinstall the core again?
Is there some problem with the installation of lucid and compiz initially which causes hardware conflicts, or is it just that we are installing new compiz core altogether for video card compatibility.
Anyways I am changing the header to SOLVED...
@[fabricator4]("http://ubuntuforums.org/member.php?u=761043")
thank you for your suggestion too.

HUMANITY TOWARDS ALL !!!!!
Regards.

LOL...Glad it worked for you tech_freak & You're quite welcome!

---

