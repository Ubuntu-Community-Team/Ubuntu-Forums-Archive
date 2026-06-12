---
title: "Can't get ANYTHING to work right"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by JoeGoe on 2010-05-01
Okay,

So I tried upgrading to Lucid, but my computer shut down during the process and then refused to boot.  I then reinstated Karmic hoping to then try upgrading again.  During the installation bcm43xx-fwcutter failed to be installed, then network manager said it didn't have the resources to continue.  Finally, after the installation from Hell was over Ubuntu said that some items failed to install.  This might leave your system unusable.  After that I connected my Ethernet cable, and that worked, however wireless is not working!  I shut down my computer, Dell Vostro 1400, and I am now afraid to turn it back on.  PLEASE HELP ME!!!!



EVERYTHING WORKS AGAIN DEAD THREAD!!!

---

### Post by jrothwell97 on 2010-05-01
I strongly suggest that if you're having this much trouble upgrading from Karmic, you should try doing a fresh install of Lucid. Download the new Live CD and do a clean install from that.

---

### Post by Rasa1111 on 2010-05-01
> **jrothwell97 said:**
> I strongly suggest that if you're having this much trouble upgrading from Karmic, you should try doing a fresh install of Lucid. Download the new Live CD and do a clean install from that.

 good advice,
 and it's faster to.:KS

---

### Post by RyanBFS on 2010-05-01
I'd go with a fresh install again, maybe boot from a CD and run the mem test then re partition the HD.  It may be that your memory had some garbage in it that caused the problem on the 2nd install... but not my area of expertise by any means.

Burn the CD _SLOWLY_ and check the md5sum [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by JoeGoe on 2010-05-01
> **jrothwell97 said:**
> I strongly suggest that if you're having this much trouble upgrading from Karmic, you should try doing a fresh install of Lucid. Download the new Live CD and do a clean install from that.
I've tried that, but when I burn it on my Mac it says could not verify disk is unreliable.

---

### Post by -humanaut- on 2010-05-01
> **JoeGoe said:**
> I've tried that, but when I burn it on my Mac it says could not verify disk is unreliable.

You need to redownload and reburn it probably make sure youre burning it at the slowest possible speed.

---

### Post by JoeGoe on 2010-05-01
I think maybe I'm using the wrong disk.  What kind of CD/DID do you guys use?

---

### Post by jrothwell97 on 2010-05-01
How are you downloading the CD image?

I strongly suggest using BitTorrent for this, since as well as being faster it'll also check for errors in the download automatically.

---

### Post by RyanBFS on 2010-05-01
it's doubtfull that it's the wrong kind of disk, just about any normal 700mb cdr disk should work that I know of.  I'd be more suspecissous of the way that the cd is being written, cd burners increase the speed that they are burrning at, in part, by not being as thourough.  Also TCP/IP is not perfect and you could have some corrupted data from the downloaded ISO so download again and check the md5sum from my link above.

---

### Post by alexcckll on 2010-05-01
Why not just buy the CD?

---

### Post by RyanBFS on 2010-05-01
They sell Ubuntu CD's in the UK? That's cool... I'm going to have to get one for my rear view mirrior :biggrin:

> **jrothwell97 said:**
> How are you downloading the CD image?

I strongly suggest using BitTorrent for this, since as well as being faster it'll also check for errors in the download automatically.

Very good point! but make sure it's a trusted source, it's very easy for people to modify open source software and put whatever they want inside it.

---

### Post by jrothwell97 on 2010-05-01
> **RyanBFS said:**
> They sell Ubuntu CD's in the UK? That's cool... I'm going to have to get one for my rear view mirrior :biggrin:



Very good point! but make sure it's a trusted source, it's very easy for people to modify open source software and put whatever they want inside it.

That's the beauty of BitTorrent: it's very difficult for anyone to slip malicious code in, providing the torrent file you use (probably, in the OP's case, one from [here](http://www.ubuntu.com/getubuntu/downloadmirrors#bt))is safe.

Error detection and correction also extends to malicious tampering. (The computer just sees these as another hash failure, and sends for the block of data again.)

---

### Post by RyanBFS on 2010-05-01
> **jrothwell97 said:**
> That's the beauty of BitTorrent: it's very difficult for anyone to slip malicious code in, providing the torrent file you use (probably, in the OP's case, one from [here](http://www.ubuntu.com/getubuntu/downloadmirrors#bt))is safe.

Error detection and correction also extends to malicious tampering. (The computer just sees these as another hash failure, and sends for the block of data again.)

Yah, Guess the only way that it's likely is if the file that all are using is manipulated.  I'm a bit paranoid lol.  Most of the offices I service can and _will_ find a way if I don't disclose every possible threat.  But... servicing over 100 ubuntu machines and not a virus yet ;) .

---

### Post by JoeGoe on 2010-05-01
Guess what?!!? I had the guts to reboot and now everything is okay!!!

Thanks for all of your suggestions!

---

### Post by Rasa1111 on 2010-05-02
> **JoeGoe said:**
> Guess what?!!? I had the guts to reboot and now everything is okay!!!

Thanks for all of your suggestions!

 Awesome Joe! :P
congrats! nice work. 
hope you like it as much as i do. <3

---

### Post by kaldor on 2010-05-02
If you have too much trouble, use Shipit and get your free Ubuntu CD. 

For the future, I highly recommend not doing upgrades unless it's a server. Never seems to work out well on the Desktop!

---

