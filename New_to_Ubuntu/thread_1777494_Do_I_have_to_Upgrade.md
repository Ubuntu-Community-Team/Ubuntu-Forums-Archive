---
title: "Do I have to Upgrade?"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by PJBradbury on 2011-06-07
I have two computers running with Linux. One with 10.04 and one with 9.04. 10.04 works fine now (after messing with it) but I cannot use xdmcp with it.

9.04 works perfectly on my older machine and runs great thru xdmcp (which I use all the time to remote access it).

9.04 is no longer supported and I run my Web server and SFTP server on it. I want to keep using xdmcp and so I do not want to upgrade. Will I have security issues or other compatibility issues if I don't upgrade?

---

### Post by IWantFroyo on 2011-06-07
You won't have the newest software. You might be accidentally downloading Windows viruses if you don't have the newest version of a browser (and other networking software), so there is actually a security risk, although you'd have to run the viruses in WINE to get them to damage your system :roll:

---

### Post by jramshu on 2011-06-07
A friend of mine runs 8.04 and refuses to change. 

He says, "If it ain't broke don't fix it."

I told him about the newer versions and he says he may look into it.

EDIT: Not saying that's what you should do.

---

### Post by LowSky on 2011-06-07
Everyone always talks about security issues, but what issues can you have if you run a firewall and block all but the unnecessary ports.

If it works, and you don't mind the out of date software, then stick with it. If you want the newer stuff, upgrade.

---

### Post by PJBradbury on 2011-06-07
Thanks, makes sense. As my computers get older I switch them over to Linux and the first time I did it ( ver 5.04) everything went smooth and the best release I ever had was 8.04. It seems that with every release since then, something has stopped working or was a pain to get working again. I don't even like the new Grub which is running on the 10.04 machine. Now that 9.04 *Jaunty* Jackalope is up and running so nicely (and I can use XDMCP I would rather not change anything. Guess I will just live with it for now.

---

### Post by FormatSeize on 2011-06-07
> **PJBradbury said:**
> 9.04 is no longer supported and I run my Web server and SFTP server on it. I want to keep using xdmcp and so I do not want to upgrade. Will I have security issues or other compatibility issues if I don't upgrade?
You may not run into any bad security issues if you are extremely lucky, and that's far too much to risk. For something like a web server, it's definitely advised that you upgrade to something that is supported.
 
I used 9.04 and refused to change until someone on these forums explained that no longer supported included no more security updates as strong as more recent releases had (I thought "no longer supported" only meant that there was going to be no new development work on the packages, and didn't really think about security). Right now I'm using 10.04, and probably will until it's no longer supported.
 
But it's not necessary to upgrade for no other reason than there's a brand new release.

---

### Post by jtarin on 2011-06-07
Have upgraded the kernel recently?

---

### Post by twopointfour on 2011-06-08
If you want to not upgrade frequently, I would definitely at least upgrade to the latest LTS version (in this case, 10.04). That's what LTS (Long Term Support) is for, people who don't want to fix things that aint broken, but still don't want to get hacked. It's officially supported until April 2013, but the next LTS version will be 12.04.

There's more real security risks than downloading viruses. If you're using this as a server that faces the internet, it probably will get hacked. If your web browser has security bugs in it most likely the worst that will happen is you'll download a Windows virus, but it's also possible you might stumble upon something targeting linux, and it also just in general leaves you and your network more vulnerable for targeted attacks.

---

### Post by Mark Phelps on 2011-06-08
What I would suggest is that you burn a CD of the latest Ubuntu version and run from it in LiveCD mode (Try, not Install).

Newer versions are NOT just upgrades and improvements to older versions; instead, in some cases, Canonical has outright replaced previous stuff with other stuff.  And, if you're used to the previous stuff -- you may not like the new stuff.

A recent example is replacing the default Gnome desktop with Unity -- a move I personally strongly dislike.

As to the security risk -- get real! While it IS possible for a Linux PC to get infected, the likelihood of this actually happening is so low as to be ignored.

Editorial comment: We can't (in one breath) go around bragging about how SAFE Linux is because of its virtual lack of malware, and then (in the next breath) try to scare folks into upgrades they don't want with threats of malware.

So, basically, if you like the new stuff, then do the upgrade.  But understand -- unlike with MS Windows, there is NO ROLLBACK capability; that is, if you don't like it, or if you encounter serious problems, you can't restore BACK to your previous version.

---

### Post by Paqman on 2011-06-08
> **LowSky said:**
> Everyone always talks about security issues, but what issues can you have if you run a firewall and block all but the unnecessary ports.


You could have a security bug in the software you have installed and working. No amount of firewalls and closed ports will protect you from an exploit in software that you need to have connecting to the internet.

If you aren't getting updates then it's only a matter of time before you get pwned by some script kiddy.

---

### Post by donkyhotay on 2011-06-08
You don't *have* to upgrade, just be aware the software you're running will become out of date and (possibly) become incompatible with newer versions. Usually it's not a big deal though unless you're swapping obscure file formats with someone else.

---

### Post by Brushstroke on 2011-06-08
As someone else said earlier in this thread, I would *at least* upgrade to 10.04 if I were you. For your server, anyway. Personally, I'm using 10.04 now because I didn't like Unity and still wanted a stable system. It works really well for me now and I'm happy with it.

---

### Post by Junkieman on 2011-06-08
While you won't risk much virus/trojan infections, I would look up the versions of the web + sftp servers you run, and check with their respective dev/support sites to see which security patches you might have missed since.

I highly recommend that, it could determine if you upgrade. You may be running up-to-date versions already not to upgrade.

**Here's what I would do: **

- Ready an external drive with enough free space > your 9.04 disk.

- Use [dd to image your 9.04 disk]("https://help.ubuntu.com/community/DriveImaging#Creating Disc Images Using dd"), byte-for-byte to a file onto the external (ignore the gzip stuff to favor speed over space).

    *You can then easily restore your disk state, byte-for-byte, if you don't like what you have done, from a Live environment.*

- copy all your config files (web/sftp/others) to the external too so you can easily copy them over to the new install.

- install 10.04 clean *(As you can [upgrade from one LTS to another]("https://help.ubuntu.com/community/LucidUpgrades"), 9.04 is not a LTS release, as such you'd need to upgrade to 9.10 LTS first, then to 10.04. It would be easier to install a clean system IMHO)*

- get [xdmcp working]("http://ubuntuforums.org/showthread.php?t=1471703"), [see here too]("http://www.remyvd.com/Set_up_XDMCP_connection_on_Ubuntu_10.04_LTS_and_log_in_with_a_Windows_domain_user"), [and here as well]("https://wiki.ubuntu.com/xdmcp"). 

- After a week of no success (or however long your patience can stretch), you can restore the 9.04 disk image to go back to that state.

Yes it may seem like a mission. But you will learn a lot, and if it works you will feel like a rock star :guitar:

To go one step further, you could recreate this setup on a virtual machine and test if everything works, but I know it's not the same as hardware and depends on the goal.

Remember: **Backup**! Image your disk, rsync all your home files too - The department of redundancy department cannot recommend this enough!

---

### Post by twopointfour on 2011-06-08
> **Mark Phelps said:**
> As to the security risk -- get real! While it IS possible for a Linux PC to get infected, the likelihood of this actually happening is so low as to be ignored.

Editorial comment: We can't (in one breath) go around bragging about how SAFE Linux is because of its virtual lack of malware, and then (in the next breath) try to scare folks into upgrades they don't want with threats of malware.

It's true you're computer probably won't get infected by malware, even if you're running outdated software. But if you're running outdated server software that anyone on the internet can connect to (like a web server), then chances are you will get hacked if you haven't already. People scan the internet for outdated linux servers and use the already-existing exploits to hack them. It happens to everyone who runs a linux server.

The reason there is so much malware for Windows is because there are so many people who use Windows that it's the obvious target to write malware for. But in the same way, a lot of people use linux servers, so hackers have put a whole lot of time into writing exploits for linux server software. Because of this, doing security updates in linux is very important. To illustrate my point, here are 15 pages of ready-to-use remote exploits for linux server software: [http://www.exploit-db.com/search/?action=search&filter_page=1&filter_description=&filter_exploit_text=&filter_author=&filter_platform=16&filter_type=3&filter_lang_id=0&filter_port=&filter_osvdb=&filter_cve=](http://www.exploit-db.com/search/?action=search&filter_page=1&filter_description=&filter_exploit_text=&filter_author=&filter_platform=16&filter_type=3&filter_lang_id=0&filter_port=&filter_osvdb=&filter_cve=)

Canonical doesn't provide updates to older versions of Ubuntu, except for the LTS versions. You can use the LTS version for 3 years and continue to stay up-to-date.

---

### Post by ivanovnegro on 2011-06-08
As mentioned yet enough times I recommend to go for 10.04, obviously its an LTS version.
If you are slow with the new stuff, thats the best option for a slower progress with the least issues.
You could stay anyway on the old version with some downsides also mentioned.
But I really think 10.04 is the way to go, its a really good and reliable Ubuntu option with support until 2013, I think thats what you need in your case, especially with a server, and when I am not wrong if you install the server version explicitly you will have even two years more support.

---

### Post by Paqman on 2011-06-09
> **twopointfour said:**
> 
Canonical doesn't provide updates to older versions of Ubuntu, except for the LTS versions. You can use the LTS version for 3 years and continue to stay up-to-date.

It's actually five years for the server release. Dapper (6.06) only just went end-of-life at the start of the month. So Lucid is good until 2015, by which time we'll all have flying robot dogs and live on the moon anyway.

---

### Post by beew on 2011-06-09
If you use really old hardware and don't mind using museum piece softwares that aptly  go with it you should check out Centos.

---

