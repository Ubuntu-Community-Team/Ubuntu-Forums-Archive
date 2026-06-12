---
title: "Install woes"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Buffboy on 2010-05-23
I've been messing with linux off & on for a few years but am for practical purpose a newbe.

I had a problem when I installed gOS (8.04)the last time on my machine. I fomatted and wound up installing on a partial hard drive partition. The result was a hard drive with very little space. I went to install backups after a couple weeks of trying out the system and that's when I discovered my error. No problem, I attempted to reinstall, this time using the whole hard drive. Problems developed that Thunderbird was unusable, downloading and installing 3 did not fix it. 

Phooy, I've got a 9.10 Ubuntu disk I put on the step-daughter's machine the night before. On my machine it gets to the partition page then just stops. Through looking in these forums, it seems my raid controller is the problem. I have one 160 gig hard drive. The motherboard bios requires that I install it's control software before it will recognise any hard drive. **Will the alternate install version of 9.10 fix this problem?** Will the new version 10.04 work with my computer? I want just one partition using the whole drive (or significant portion). The gOS I put back on this machine installed itself on a small partition of the hard drive again, leaving an unmounted 145 gig ext3 partition I'd created empty and it's unusable by gOS. I spent 6 hours trying to get an OS back on this machine yesterday and I'm worse off than before.

---

### Post by Vincentlaborant on 2010-05-23
I think you will have to use the alternate CD of Ubuntu 10.04 LTS. Only the alternate installation will let your raid configuration properly.

I had the same problem and fixed this by using the alternate cd to install ubuntu 10.04 LTS

---

### Post by themusicalduck on 2010-05-23
Boot up the 9.10 live CD and open a terminal (Applications > Accessories > Terminal). Run this command ```
sudo apt-get remove dmraid
``` and then try running the installer. Hopefully it'll recognise your raid then.

I think you need to do the same if you use 10.04.

It's likely that 10.04 would work with your PC. It's a really good release and is LTS so it will be supported with updates for 3 years, whereas 9.10 is supported for another year I think.

---

### Post by Vincentlaborant on 2010-05-23
> **themusicalduck said:**
> Boot up the 9.10 live CD and open a terminal (Applications > Accessories > Terminal). Run this command ```
sudo apt-get remove dmraid
``` and then try running the installer. Hopefully it'll recognise your raid then.

I think you need to do the same if you use 10.04.

It's likely that 10.04 would work with your PC. It's a really good release and is LTS so it will be supported with updates for 3 years, whereas 9.10 is supported for another year I think.

Normal releases are supported for 18 months, LTS for 36 months. Ubuntu 9.10 will receive updates  till  06 2011. It can take you till Ubuntu 11.04 if you want to play it safe with a RAID configuration (assuming it works on your 9.10 install and not on 10.04).

---

### Post by Buffboy on 2010-05-23
I used the Alternate 10.04 CD. The only way I could get **to** the disk manager **at all** was to tell it to ignore raid. It installed the program into a 3 gig partition of the 145 Gigs I told it to make. After installation I have 10 megs of drive space, 135 gigs of unmounted and unusable hard drive.  So much for Alt. It did the same as the gOS, left me with something to browse the net and totally unusable for anything else.  I don't want a netbook.

Edit: I'll try to install again using the Sudo Command.

---

### Post by Buffboy on 2010-05-23
I had no room to download and run the standard 10.04 ISO(not enough disk space) so I couldn't try themusicalduck's idea with 10.04. I tried the 10.04 Alternate Install CD again before attempting to use his idea with a 9.10 disk. This time, it still wouldn't run my raid, so I used the "don't use" option and this time got the option to use the whole disk(it wasn't an available option the first time, don't know why). It formatted and installed normally. I don't know what the problem was but it seems to have installed normally this time. Updates ran fine, everything seems to work, and I have space again. Thank you for your help.

---

