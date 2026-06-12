---
title: "how to get rid of windows virus from ubuntu?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by fremantle on 2010-06-23
my windows is infected with some kind of malware. this is what happens:

Whenever i search something on yahoo, google, bing _ if a click on a search result, instead of taking me to the linked webpage, i get redirected to some random advertising website. I can access the search result pages if i left click > copy the link and paste it in a separate navigation bar. I have AVG AnitiVirus 9 updated. I tried IE, Chrome, Firefox, Safari, Opera - same thing happens to all. Also: I cannot go to some antivirus websites, for example: AVG.com or TrendMicro's official website. But i can access them via proxy.

What i tried: I ran scans using my AVG, NOTHING. Then i looked up forums where i saw people with the same problem got rid of it using a program called Trojan Remover. Than, i had to download it using proxy and ran a scan. The scan showed 2 DNS-something trojan that "redirects you to malicious webpages instead of the linked ones". So, i removed them and restarted my pc. No sh*t happened.

Fortunately i had ubuntu dual booting and on ubuntu i am not facing that problem. I heard that you can remove windows viruses using ubuntu. How can i get rid of my one?

---

### Post by lisati on 2010-06-23
You might want to check out the free Linux-based AVG rescue CD
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by KdotJ on 2010-06-23
Hey, 
My mother had the same issue on her windows machine. It is often referred to as the "Google Redirect Virus" but obviously is not purely just with Google.

Anyways, I managed to solve it by running a program called Hitman Pro

You can download it for free from cnet [HERE]("http://download.cnet.com/Hitman-Pro-3/3000-2239_4-10895604.html")

It is safe, does not contain a virus/malware etc

Just install it, run it, then follow the instructions to removed the infection. I think a reboot is required after.

Good luck, report back if you can

[Edit]
Do this in Windows

---

### Post by fremantle on 2010-06-23
> **lisati said:**
> You might want to check out the free Linux-based AVG rescue CD
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)
Why? I just want to get rid of a simple infection not recover my whole system

---

### Post by fremantle on 2010-06-23
> **KdotJ said:**
> Hey, 
My mother had the same issue on her windows machine. It is often referred to as the "Google Redirect Virus" but obviously is not purely just with Google.

Anyways, I managed to solve it by running a program called Hitman Pro

You can download it for free from cnet [HERE]("http://download.cnet.com/Hitman-Pro-3/3000-2239_4-10895604.html")

It is safe, does not contain a virus/malware etc

Just install it, run it, then follow the instructions to removed the infection. I think a reboot is required after.

Good luck, report back if you can

[Edit]
Do this in Windows

wow man thanks a lot!! :D im going to try that. Does it also get rid of the fake antivirus malware? you know, the one that stops opening any .exe and accessing Internet unless you "buy" the "pro" version of a "antivirus"

---

### Post by sb5551 on 2010-06-23
Depending on what web browser you are using just clear the cache and history and stuff. Sometimes a virus can be inadvertently stuck in there. If it is a windows machine you are using I recommend CCleaner. If its Ubuntu I recommend Bleachbit.

---

### Post by fremantle on 2010-06-23
> **sb5551 said:**
> Depending on what web browser you are using just clear the cache and history and stuff. Sometimes a virus can be inadvertently stuck in there. If it is a windows machine you are using I recommend CCleaner. If its Ubuntu I recommend Bleachbit.

No, that does not work. i used YourUninstaller Pro to clean internet traces and delete temp files. Than i used tuneup utilities to completely clean and defragment the windows registry. After than manually cleared firefox's browsing data. Absolutely NOTHING happened.

---

### Post by KdotJ on 2010-06-23
> **fremantle said:**
> wow man thanks a lot!! :D im going to try that. Does it also get rid of the fake antivirus malware? you know, the one that stops opening any .exe and accessing Internet unless you "buy" the "pro" version of a "antivirus"

I'm not sure what else it will pick up, but it should sort your problem out. I tried everything on my mum's machine (empting cache etc), but this worked.

---

### Post by lkraemer on 2010-06-23
Check out:
[http://ubuntuforums.org/showthread.php?t=1463709&highlight=virus](http://ubuntuforums.org/showthread.php?t=1463709&highlight=virus)
Posting #9.

lk

---

### Post by k3lt01 on 2010-06-23
Install the FireFox Add-On "Redirect Cleaner", make sure it is enabled and see how you go.

---

### Post by wilee-nilee on 2010-06-24
Try superantispyware.
[http://www.superantispyware.com/](http://www.superantispyware.com/)
Really you have to run a cleaner from safemode to get things out at times. Download it and run it from the safe mode.
This a good one as well.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
Also a excellent file cleaner.
[http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)

Also are you using a limited account or admin?

---

### Post by Hendronicus on 2010-06-24
I cleaned one of these off of a friends machine by first determining the name of the process. To do that, I simply ran msconfig and looked for any suspicious names that were running at start-up. Then, I disabled that program. To completely clear it off, I booted Linux from a thumb drive and deleted the program because Vista wouldn't let me delete this "protected" file. It worked quite well and they haven't had any problems with it since.

---

### Post by wilee-nilee on 2010-06-24
> **Hendronicus said:**
> I cleaned one of these off of a friends machine by first determining the name of the process. To do that, I simply ran msconfig and looked for any suspicious names that were running at start-up. Then, I disabled that program. To completely clear it off, I booted Linux from a thumb drive and deleted the program because Vista wouldn't let me delete this "protected" file. It worked quite well and they haven't had any problems with it since.

That is haphazard advice one of those could be a million possibilities.

---

### Post by Hendronicus on 2010-06-24
And running some dodgy junk from the web is somehow better?

---

### Post by Andrew-J on 2010-06-24
Did you fix it?

I could be wrong i think you can download and run antivirus/malware off of your live cd. I would try to find one that can scan by partition.

---

### Post by wilee-nilee on 2010-06-24
> **Hendronicus said:**
> And running some dodgy junk from the web is somehow better?

The ones I suggested are not dodgy there are some of the best, especially superantispyware, you don't have a clue.

for just your information I several friends that are certified in Apple, Windows, and Linux and make a living cleaning and repairing computers these are what they use, along with comodo, avast, spybot, amongst others. I don't just post junk I think works but solutions that are known to work.

---

### Post by Hendronicus on 2010-06-24
> **wilee-nilee said:**
> The ones I suggested are not dodgy there are some of the best, especially superantispyware, you don't have a clue.


Yeah, with a name like that I'm sure it's really great. /s

Anyway, did you even read what I wrote? I used Windows itself to fix it. He's got a TROJAN!!! not a virus. It's easily fixed without installing anything. You don't need to be insulting either.

---

### Post by lisati on 2010-06-24
> **fremantle said:**
> Why? I just want to get rid of a simple infection not recover my whole system

Forum rules prevent me from giving an honest response, so I will have to content myself with this: No, it is a RESCUE CD that can deal with infections, not a CD to recover your whole system.

---

### Post by wilee-nilee on 2010-06-24
> **Hendronicus said:**
> Yeah, with a name like that I'm sure it's really great. /s

Anyway, did you even read what I wrote? I used Windows itself to fix it. He's got a TROJAN!!! not a virus. It's easily fixed without installing anything. You don't need to be insulting either.

If you took the time to look at it you would understand its use. Rather than reacting in a emotive manner.
[http://www.superantispyware.com/trojans.html](http://www.superantispyware.com/trojans.html)

It is only insulting if you perceive it to be, it was not intended to be.

From the web page
> Detect and Remove Spyware, Adware and Remove Malware, Trojans, Dialers, Worms, KeyLoggers, HiJackers, Parasites, Rootkits, Rogue Security Products and many other types of threats.

---

### Post by dtfinch on 2010-06-24
Some malware is too lazy to change its file modified date, so you can find all the exe, dlls, and other executables modified at the time the malware was installed and rename any that look suspicious, assuming it didn't modify something vital that already existed.

---

### Post by questioning on 2010-06-24
awesome windows fanboy thread on this ubuntu forum here.

:popcorn:

---

### Post by Hendronicus on 2010-06-24
@dtfinch: That is exactly how I found that one. It took about ten seconds. Even if you disable something that you want, you can just re-enable it later. My way is safe and easy.

@wilee-nilee: I do this for a living, and I've been doing it for quite some time. I don't care how many certs you or your friends have.

---

### Post by Hendronicus on 2010-06-24
> **questioning said:**
> awesome windows fanboy thread on this ubuntu forum here.

:popcorn:

It is pretty funny. I'm sorry I even know how to get rid of one of these. :lolflag:

---

### Post by wilee-nilee on 2010-06-24
> **Hendronicus said:**
> @dtfinch: That is exactly how I found that one. It took about ten seconds. Even if you disable something that you want, you can just re-enable it later. My way is safe and easy.

@wilee-nilee: I do this for a living, and I've been doing it for quite some time. I don't care how many certs you or your friends have.
If you want to argue feel free to Pm me, at this point the OP is the one that needs help.

---

### Post by netwarriorwy on 2010-06-24
Hendronicus: I think your way of solving the problem is quite nice. Btw I understand that you may not trust on @wilee-nilee solutions (using software) and I know why, its because a lot of times there are so called "anti-malware" softwares that the only thang they do is infect u more, but but but XD given the experience @wilee-nilee says he has, we gotta trust him, THE IMPORTANT THING HERE as stated by @wilee-nilee IS TO HELP the OP, cause who knows maybe neither solution will work for him, but I hope someone does

---

### Post by k3lt01 on 2010-06-24
> **wilee-nilee said:**
> If you took the time to look at it you would understand its use. Rather than reacting in a emotive manner.
[http://www.superantispyware.com/trojans.html](http://www.superantispyware.com/trojans.html)

It is only insulting if you perceive it to be, it was not intended to be.

From the web pageI can't help but jump in here, you have a habit of being insulting, you have a habit of telling people to do things without explaining why they should do it, you have a habit of reacting emotively yet you tell others not to. You wont take this advice but I will give it anyway, take a look at how you deal with people, you are NOT the only person who knows how to do things.

Your insults are childish, your claims of being able to help because you know multiple people who have multiple certificates is something you cannot prove so it is baseless. In other words most of the things you say is smoke and mirrors. You REALLY need to start to think about these things, instead of bludgeoning people with your baseless facts. Everyone else cannot be wrong all the time.

Last thing, before you think of PMing me and calling me a moron AGAIN I'd take a second to think about putting your thoughts in a nicer way.

---

### Post by mal1958 on 2010-06-24
And here is a bit of advice with Firefox (if you don't already have this one that is)  Get the Add on _**No Script**_.  It works wonders to keep these things from hitting you again.

---

### Post by Rubi1200 on 2010-06-24
Regarding prevention:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and especially:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by AjC41 on 2010-06-24
ok boot up in safemode with networking, download Malware Bytes Anti Malware. and do a full system scan. it will get rid of the problem. and then download CCleaner and clean everything up like registry and stuff.

---

### Post by KdotJ on 2010-06-24
All arguing aside lol....

did the OP fix the issue with one of the suggestions?

---

### Post by fremantle on 2010-06-24
guys...! stop arguing.

i solved the prob. did anyone of you mentioned[ ComboFix]("http://combofix.org")? First i tried the Hitman thingy someone recommended, it did pick up malwares and removed them, but the problem was still there. Then after a long forum searching i got combofix (never heard of it before). I have to admit its a pretty nice program. I ran it in safe mode and followed all instruction and restarted my pc. Then, the fake antivirus was gone. And, the search-redirect malware i think was removed, BUT two or three times it did happen again (what am i gonna do?)

Another thing,, my internet got SUUUPER SLOWW.. i use 2mbps dsl but it works like a freakin dial-up connection.. im really messd up here.. But im sure its JUST windows, cause on ubuntu the internet is same as always. What i wana know is that is there any antivirus FOR linux that will scan the host windows files and dlt the malware???? man i cant go thru reinstalling xp again, coz to reninstall xp, i'll have to uninstall ubuntu too....

---

### Post by wilee-nilee on 2010-06-24
Here is what wot says about your combofix link.
[ATTACH]161480[/ATTACH]

Download the link to superantispyware in Ubuntu put it on a thumb boot windows drag it to the desktop install it and do a full scan after updating if it will.
[http://www.superantispyware.com/](http://www.superantispyware.com/)

Edit I will add here that using this program is not a fix all, but should get rid of some problems. Others psoted good solutions including using the Ubuntu side or a live cd to remove the ware. 

Honestly not knowing how you got this stuff in the first place and not knowing if your running in a admin=root account rather then a limited account it is really unknown what you have been exposed to. If was me I would back up the important stuff and reinstall XP then scan all the backed up before putting it back in.

If you have been running in admin you could also have rootkits and keyloggers...etc, and some can't even be detected other then with a binary search, and then you have to guess which seems suspicious.

---

### Post by k3lt01 on 2010-06-24
> **fremantle said:**
> guys...! stop arguing.You don't know the history of it, all I will say is we are all trying to help.

There is a slight issue with just posting up links and saying use this or do this. Unless you the person who needs the help understand what you are doing you could infact end up with alot more trouble.

There are many fake malware scanners about and most just infect you with more while claiming to have cleaned up your system. Then you notice things like your connection being "as slow as a wet week".

I have to admit I misunderstood you initial complaint, the title isn't clear and I thought you may have had a cross platform trojan in your internet browser in Ubuntu, yes they do exist just ask an Apple expert what havoc MS Office etc has caused Apple. That is why I initially suggested, and I still stand by the suggestion, RedirectCleaner in Firefox Addons.

Now to the crux of your complaint. Boot into Ubuntu and download [SpyBot Search and Destroy]("http://www.safer-networking.org/"). When you have got it, copy it to a flash drive or something, boot into Windows in Safe Mode and install SpyBot, update it, and run the test. It will probably tell you that you have a few problems and that it needs to run the test at next startup. LET IT do this as it needs to clean your system BEFORE anything else loads. I'll be honest this can take quite a while to fix but SpyBot will fix it.

---

### Post by wilee-nilee on 2010-06-24
The spybot link is another excellent cleaner.;)

The only thing  would add here is if your getting redirected the best way to get these cleaners in is to download the install programs in Ubuntu put them on a thumb or drag them to the XP desktop, by opening the partition. Personally I wouldn't open the partition but it is a option.

---

### Post by k3lt01 on 2010-06-25
Not being critical but I don't actually see how he has an option using something like SpyBot and NOT going into Windows to get it to install. I tried last year back on 9.10 to install SpyBot via WINE and see if I could work it that way, my former employer had a severe infection on the main machine at my former place of employment so I tried doing this to try to avoid actually opening Windows but it wouldn't work. Anyway cutting a long story short it took most of the day, yes the infection was that bad, but I did get it installed on Windows relatively quickly and then I let it do its thing.

Also I agree not knowing how the infection come about makes it difficult for us to understand the depth of the problem and be able to give definitive advice. I'm now working from a worst case scenario, not trying to apportion blame or anything it just makes it easier to work through if you expect the worst, and guessing that the system is infact severely compromised just like the machine I mentioned earlier in this post. The easiest thing may be to just do a clean re-install of Windows and then copy the backed up file back over. The issue I see that unless something like SpyBot is installed before the backed up file are replaced then the infection may take hold again.

Remember prevention is better than cure, it is cheaper and takes alot less time.

---

### Post by wilee-nilee on 2010-06-25
> **k3lt01 said:**
> Not being critical but I don't actually see how he has an option using something like SpyBot and NOT going into Windows to get it to install. I tried last year back on 9.10 to install SpyBot via WINE and see if I could work it that way, my former employer had a severe infection on the main machine at my former place of employment so I tried doing this to try to avoid actually opening Windows but it wouldn't work. Anyway cutting a long story short it took most of the day, yes the infection was that bad, but I did get it installed on Windows relatively quickly and then I let it do its thing.

Also I agree not knowing how the infection come about makes it difficult for us to understand the depth of the problem and be able to give definitive advice. I'm now working from a worst case scenario, not trying to apportion blame or anything it just makes it easier to work through if you expect the worst, and guessing that the system is infact severely compromised just like the machine I mentioned earlier in this post. The easiest thing may be to just do a clean re-install of Windows and then copy the backed up file back over. The issue I see that unless something like SpyBot is installed before the backed up file are replaced then the infection may take hold again.

Remember prevention is better than cure, it is cheaper and takes alot less time.

No problem all you down load with these is the .exe file that installs the program, it can be downloaded in Ubuntu if a person has a redirect problem and put on the XP desktop, via through the partition or from a thumb. I haven't checked if this is the case with spybot but I will right now.

I wasn't suggesting a wine or Ubuntu install just getting the .exe install file for installation if there is a redirect problem.

The spybot .exe downloaded fine to Ubuntu. I use this method as I have fixed friends computers that were so infected that you couldn't download a cleaner to them, some wouldn't even let the browser work in Widows whether IE, FF, Chrome, or Opera. 

One friends had 386 hits with superantispyware, it was destroyed anyway after cleaning it I just reinstalled XP for them and set them up with a limited account using FF with noscript, betterprivacy, ghostery, wot, adblock plus, avast, malwarebytes, ccleaner and superantispyware not a problem since.

I agree with the reinstall, and I would only back up the media and scan it first with every thing I had before adding it back.

---

### Post by wilee-nilee on 2010-06-25
Is Ubuntu a wubi install? if it isn't you can reinstall XP without removing Ubuntu. You just have to reinstall Grub to the MBR.

I think the combofix was a spyware introducer not a cleaner. Wot reports the site as I showed, and Wot is a respected FF addon warning, used by Windows users, and recommended on the W7 forums as a website warning. 

Edit It may be that the combofix was legit but there is just more in there or damage done.

---

### Post by fremantle on 2010-06-25
i gave up. just wiped off xp and installed my copy of vista.:lolflag:

---

