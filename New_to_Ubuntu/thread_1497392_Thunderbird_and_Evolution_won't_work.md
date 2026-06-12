---
title: "Thunderbird and Evolution won't work"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by flopwich on 2010-05-30
An Acer Aspire One netbook running Ubuntu 10.04.  Thunderbird and Evolution worked fine under Ubuntu 9.10, but ever since the upgrade I can't get them to work properly.  Occasionally they'll work just fine, but most of the time I get "connection refused" or "connection timed out" on trying to access my email with my local ISP, and "connection refused" on trying to get email off my Gmail account.  Evolution came up with the new wrinkle today of having the "Send/Recieve" button grayed out on the toolbar, so I can't access it.

Firefox is working just fine, and I have another Acer Aspire One on which I still have v9.10 and both Evolution and Thunderbird are working fine there, using the same wireless configuration and ISP and accessing the same accounts with which they won't work on the other computer.

Help would be greatly appreciated.

---

### Post by dunbrokin on 2010-05-30
I have a similar problem....just upgraded today....TB will no longer access my mail or calendar.

---

### Post by Autodave on 2010-05-30
> **dunbrokin said:**
> I have a similar problem....just upgraded today....TB will no longer access my mail or calendar.


Don't know if this will help or not, but check your settings again.  My update to 10.4 changed both of my port settings.  Putting them back let TB work just fine.

---

### Post by dunbrokin on 2010-05-30
Hmmm, I suspected that might be the problem....but I don't know what they were before!!

---

### Post by Autodave on 2010-05-30
> **dunbrokin said:**
> Hmmm, I suspected that might be the problem....but I don't know what they were before!!

You'll have to go to the website for all of your email accounts and find out what their ports are.  Also, you need to know all the rest of the settings such as POP, IMAP, etc.  When you get the info, print it and put it in a folder somewhere that you won't lose.  Trust me on this one: after redoing mine the second time, I learned to keep a written record. :-)

---

### Post by dunbrokin on 2010-05-30
OK, I have got the various ports, pop, smtp etc from another machine on my home network which has not upgraded yet to 10.04. I have put them in both Thunderbird and Evolution and neither of them can access my mail box. TB cannot access the Google calendar either...whereas Evolution can.

Weird or what?....Any help much appreciated. I was just about to reinstall TB when I decided to check Evolution...and found it had the same problem I do not have a firewall installed.

---

### Post by Autodave on 2010-05-30
> **dunbrokin said:**
> OK, I have got the various ports, pop, smtp etc from another machine on my home network which has not upgraded yet to 10.04. I have put them in both Thunderbird and Evolution and neither of them can access my mail box. TB cannot access the Google calendar either...whereas Evolution can.

Weird or what?....Any help much appreciated. I was just about to reinstall TB when I decided to check Evolution...and found it had the same problem I do not have a firewall installed.


At this point, assuming that everything is set properly....and I do mean EVERYTHING....check ALL settings, I would uninstall them both.  Do a complete uninstall from Synaptic package manager making sure to delete the configuration files and start over.

---

### Post by dunbrokin on 2010-05-30
Hmmm. If both TB and Evolution are having similar problems then probably an uninstall and reinstall is not the solution. There is something else that we should be looking for I am guessing.

---

### Post by Georgia boy on 2010-05-30
I agree with AutoDave on double checking the settings. I had trouble with both when I did the wipe and install with Lucid. Come to find out I had a couple settings turned around and they were giving me headaches until I kept checking and overlooking and checking again to realize what I had done. After giving a few choice words to myself I redid the settings again and all worked fine. You might want to double check one more time on the settings just in case. 

Tom

---

### Post by dunbrokin on 2010-05-30
Hmmmm. But Evolution does not have any port choices that you can make...and it does not work either. So, it has to be something else I am guessing.

---

### Post by Autodave on 2010-05-30
> **dunbrokin said:**
> Hmmmm. But Evolution does not have any port choices that you can make...and it does not work either. So, it has to be something else I am guessing.

Evolution definitely has port choices along many other choices.  I don't use Evolution any longer since I had problems with it, but there are the same set-up parameters in Evolution as in TB.

I quit using Evolution because about once a month my settings would change for absolutely no reason at all.  I tried TB and never had a single problem until the update to Ubuntu 10.4 when the settings were changed. I put the settings back to where they should have been and it has been working perfectly since then and I had updated on the very first day 10.4 was available.

---

### Post by dunbrokin on 2010-05-30
I am thinking that the problem is not in the GUI - where the parameters all seem to be correct. I am thinking that the problem is some where in the scripts. When I updated it asked me a number of times whether I wanted to keep old scripts of programs (I can't remember which ones now!) but I always opted for the old scripts rather than the new ones.....I am thinking that there in lies the problem......but where are these and how can I access them. I have just tried now a different profile that my wife uses on my PC. She had set up TB to connect to gmail. It worked up until I changed to 10.04...now it no longer works.

---

### Post by flopwich on 2010-05-30
Yes, well, as I said, I have another Acer Aspire One running v9.1 Ubuntu and relevant versions of Thunderbird and Evolution, which work just fine, thank you very much.  I pulled those up and set all of the settings, ports and all, exactly the same.  I was able to get email from my local ISP, once.  Then I got the "connection refused" message again. 

I was unable to access my Gmail account.  "Connection refused", again. <sigh>  After the one success of accessing my local email account, "Connection refused", on that, as well.   I alternate between that message and "Timed out" on each combination of configuration I try.

Also, Evolution reports, "No route to host", even though I can ping the mail server.  This is just too weird for me to get a handle on what's going on.

---

### Post by dunbrokin on 2010-05-31
bump!

---

### Post by mastablasta on 2010-05-31
to add port in evolution you type it next to the server. example:
 
imap.gmail.com:26
 
It is a bit strange that you can not connect to server. I had a problem sending out because i didnt' add port number. now it all works (am still on Karmic).

---

### Post by lazyart on 2010-05-31
I did a clean install of Lucid, retaining my home partition.

I installed Thunderbird and it picked up all my accounts, but a couple of them could not send mail.  It turned out that Secure Authentication was turned on, but I don't think I had it turned on previously.  Go back and recheck your connection settings and be sure the ports and authentication are correct per your ISP/mail provider.

---

### Post by XubuRoxMySox on 2010-05-31
I didn't like the new Thunderbird. It auto-configured my mail settings, created about a dozen new folders and started this huge download of my entire gmail history - including the trash! C'mon, the trash??!

I stopped it, searched all over for the old Thunderbird 2.0 and couldn't find it, and ended up with **SeaMonkey** - which works just like my old Thunderbird did, including the Lightning calender extension! It's in the repositories so you can install it right from Synaptic.

It's kinda slow though. But for me the trade-off is worth it.

-Robin

---

### Post by lazyart on 2010-05-31
> **dixiedancer said:**
> I didn't like the new Thunderbird. It auto-configured my mail settings, created about a dozen new folders and started this huge download of my entire gmail history - including the trash! C'mon, the trash??!

I stopped it, searched all over for the old Thunderbird 2.0 and couldn't find it, and ended up with **SeaMonkey** - which works just like my old Thunderbird did, including the Lightning calender extension! It's in the repositories so you can install it right from Synaptic.

It's kinda slow though. But for me the trade-off is worth it.

-Robin

IMAP synchronize was the reason why.  Thunderbird has a couple tabs when you first start it up, one of which is the migration assistant.  Turn off IMAP sync from that tab.

---

### Post by mastablasta on 2010-05-31
> **dixiedancer said:**
>  
I stopped it, searched all over for the old Thunderbird 2.0 and couldn't find it, 
 
i invested 5 seconds of time and here is the link for the 2.0 version (i am still using it because it says on windows that it needs 756 MB ram to work WTF is that?):
[http://www.mozillamessaging.com/en-US/thunderbird/all-older.html](http://www.mozillamessaging.com/en-US/thunderbird/all-older.html)
 
 
 
[QUOTE=lazyart]IMAP synchronize was the reason why. Thunderbird has a couple tabs when you first start it up, one of which is the migration assistant. Turn off IMAP sync from that tab.[/QUOTE]
 
this really was a "fantastic" idea by developers. And as it appears they still didn't turn it off by default. if user has IMAP he has it for a reason and therefore he doesn't want the IMAP to be turned into POP3 account. Especially gmail (to me also known as "garbage" mail) account.

---

### Post by flopwich on 2010-05-31
this really was a "fantastic" idea by developers. And as it appears they still didn't turn it off by default. if user has IMAP he has it for a reason and therefore he doesn't want the IMAP to be turned into POP3 account. Especially gmail (to me also known as "garbage" mail) account.[/QUOTE]

So, based on that comment I went back in Thunderbird 3.0 and deleted the accounts I'd set up (because the automagic setup decided that my POP account should be IMAP and you can't change that setting any other way), then set up my main one again.  I interrupted the automagic setup routine and configured it manually to match the Thunderbird 2.0 configuration on my other computer running Ubuntu v9.1.  I was able to download my email after that, *_once_*.  I was unable to send.  Now I get "connection refused" again.  I then tried Evolution again and was able to download my email, once.  Now it refuses to work, as well, giving me both "connection timed out" and "could not connect to mail.xxx.net: no route to host."  I then tried the other computer with v9.1 immediately, in case it there really was no route to host, and was able to download and send email in Thunderbird with no problem.

Since *_both_* Evolution and Thunderbird exhibit the exact same problem, since both worked fine on here under Ubuntu v9.1 and since both failed on upgrading to the v10.04, it sure looks like the smoking gun lies with the new version of Ubuntu.  And since it seemed to reset, at least on the receive side, when I removed the account and set it up again, and it seemed to reset for both Thunderbird and Evolution, I'm guessing there's something going on with a setting somewhere on something like the network interface card that interferes with both of them, something that v9.1 didn't mess with.  Unfortunately I don't know enough about Ubuntu or Linux to look for where that setting might be.

---

### Post by dunbrokin on 2010-05-31
I am with flopwich on this one. Both TB and Evolution exhibit the same problem for me also....it must be the Ubuntu. My wife's PC has not been upgraded yet and I have followed her settings in setting up both Evolution and TB....all to no avail. I cannot receive or send on either of them using port 110 to receive and 10025 to send.All encryption SSL etc are turned off.....always get the same message "Timed out". If it wasn't for Gmail, I would be scuppered right now as I cannot contact my clients via my normal email. This is a SERIOUS problem for me....and, apparently, for a minority of other people. Any help would be much appreciated.

---

### Post by dunbrokin on 2010-05-31
> **mastablasta said:**
> to add port in evolution you type it next to the server. example:
 
imap.gmail.com:26
 
It is a bit strange that you can not connect to server. I had a problem sending out because i didnt' add port number. now it all works (am still on Karmic).

Thanks, did that....no difference.

---

### Post by flopwich on 2010-05-31
Okay, I don't know whether to cheer or throw a tantrum here.  I've gotten both Evolution and Thunderbird to work.  For some reason in the older versions of both of those, I was able to enter "username" for the user name under server settings (Thunderbird) and receiving email (Evolution), that is, without the "@domainname.net", and that worked just fine.  It happens I've got a version of Thunderbird 3.0 for Windows on a flash drive, so I checked the configuration on that and it turns out that I'd entered "username@domainname.net", that is, the full address, and it worked fine.  I went back to the Ubuntu versions of Thunderbird and Evolution and made that change in each and they now appear to work.  (I say "appear" because I'm a little twitchy at this point, but I've sent and received email several times now on each one.)

Somebody apparently made a change in either Evolution and Thunderbird in their new versions, or in Ubuntu 10.04 that now requires the full email address.  Whatever.  Give that a try and good luck!

Thanks for everybody's help.

---

### Post by dunbrokin on 2010-05-31
Does not work for me....I already had the full [email]name@domainname.com[/email] put in.

---

### Post by dunbrokin on 2010-05-31
OK, here is what I did. On an other machine running 10.04 I downloaded TB from the TB website (not repositories) and installed that. I set it up and ran it....it asked me for my password, I could not remember my password so I had to contact my ISP and  make up a new one. Once I had changed my password and entered the new password, it did not ask me for it anymore....however it still timed out. So, I believe now that it is logging into my email account but not downloading the emails.....this is definitely a Ubuntu problem I am thinking. Any suggestions?

---

### Post by dunbrokin on 2010-06-01
I have now tried with Claws Mail also...and still same result...cannot connect.

---

### Post by dunbrokin on 2010-06-01
Is there a way that I can set up some kind of log so that I can see what is happening as I try to log in.....that might give me a clue.

---

### Post by Jakiejake on 2010-06-01
> **flopwich said:**
> An Acer Aspire One netbook running Ubuntu 10.04.  Thunderbird and Evolution worked fine under Ubuntu 9.10, but ever since the upgrade I can't get them to work properly.  Occasionally they'll work just fine, but most of the time I get "connection refused" or "connection timed out" on trying to access my email with my local ISP, and "connection refused" on trying to get email off my Gmail account.  Evolution came up with the new wrinkle today of having the "Send/Recieve" button grayed out on the toolbar, so I can't access it.

Firefox is working just fine, and I have another Acer Aspire One on which I still have v9.10 and both Evolution and Thunderbird are working fine there, using the same wireless configuration and ISP and accessing the same accounts with which they won't work on the other computer.

Help would be greatly appreciated.

Whats after the @?
Who is your email with?

---

### Post by dunbrokin on 2010-06-01
Weird or what....I restarted my machine after installing a whole heap of Medibuntu stuff.....and, bugger me, the darn thing just worked....I am flabbergasted....thanks to all for the help.

---

### Post by Jakiejake on 2010-06-01
> **dunbrokin said:**
> Weird or what....I restarted my machine after installing a whole heap of Medibuntu stuff.....and, bugger me, the darn thing just worked....I am flabbergasted....thanks to all for the help.

Awesome
Good Luck With Ubuntu

---

### Post by flopwich on 2010-06-01
> **dunbrokin said:**
> Weird or what....I restarted my machine after installing a whole heap of Medibuntu stuff.....and, bugger me, the darn thing just worked....I am flabbergasted....thanks to all for the help.

Yeah, well, as I said I had both Thunderbird and Evolution working yesterday, and earlier this evening Thunderbird was working fine, again.  Now neither one is working.  Evolution tells me, again, that the connection timed out.  Thunderbird again tells me the connection was refused.  The only thing that's changed is a thunderstorm came through and I had to re-start my DSL router.  I was having trouble connecting to it with another computer.

This is horrible.  I'm getting really sick of this not working.

---

### Post by dunbrokin on 2010-06-01
You have my full sympathy. 

I went on to the [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) forum and downloaded all the medibuntu stuff and I also did [http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html) and restarted my machine.....and low and behold...all my emails worked...and are still working. 

Hope this helps.

---

### Post by flopwich on 2010-06-01
> **dunbrokin said:**
> You have my full sympathy. 

I went on to the [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) forum and downloaded all the medibuntu stuff and I also did [http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html) and restarted my machine.....and low and behold...all my emails worked...and are still working. 

Hope this helps.

Well, thank you, but I did all that and the @#$%^& thing still isn't working.  I sure wish the folks who wrote the communications handling in v10 would give us a little help here.  I'm pretty exasperated here.  Something is CLEARLY wrong with the way the new version of Ubunto (doesn't) work, but nobody seems to be offering any help with it.  I'm just about ready to uninstall it and go back to version 9.  This is just ridiculous.

---

### Post by Jakiejake on 2010-06-02
> **flopwich said:**
> Well, thank you, but I did all that and the @#$%^& thing still isn't working.  I sure wish the folks who wrote the communications handling in v10 would give us a little help here.  I'm pretty exasperated here.  Something is CLEARLY wrong with the way the new version of Ubunto (doesn't) work, but nobody seems to be offering any help with it.  I'm just about ready to uninstall it and go back to version 9.  This is just ridiculous.

Typo :lolflag:

---

### Post by mastablasta on 2010-06-02
> **flopwich said:**
> Yeah, well, as I said I had both Thunderbird and Evolution working yesterday, and earlier this evening Thunderbird was working fine, again. Now neither one is working. Evolution tells me, again, that the connection timed out. Thunderbird again tells me the connection was refused. The only thing that's changed is a thunderstorm came through and I had to re-start my DSL router. I was having trouble connecting to it with another computer.
 
This is horrible. I'm getting really sick of this not working.
 
 
Are you maybe using torrents? They can clog up the connection even after you turned off the programme.
 
Also do you have your ports open on the router? Some routers have built in firewalls.
 
So basically Thunderbird says connection timed out but at the same time internet (for example firefox) is working normally?

---

### Post by flopwich on 2010-06-02
> **mastablasta said:**
> Are you maybe using torrents? They can clog up the connection even after you turned off the programme.
 
Also do you have your ports open on the router? Some routers have built in firewalls.
 
So basically Thunderbird says connection timed out but at the same time internet (for example firefox) is working normally?

Ah, that could be a problem, as I know my router has a firewall in it.  And that is the set of symptoms.  Can you offer any information on how I would explore that?  Also, everything has worked fine with versions 8 and 9 of Ubuntu.  Would they likely have been fine with everything before now and then get hosed up?

Thank you.

---

### Post by mickpork on 2010-08-02
Hi Flopwich...did you end up getting your problem worked out? i am just asking as i seem to have the same problem and it is so frustrating.I can actually use kmail and no other email programs.Does anyone have any solutions??

---

### Post by flopwich on 2010-08-03
> **mickpork said:**
> Hi Flopwich...did you end up getting your problem worked out? i am just asking as i seem to have the same problem and it is so frustrating.I can actually use kmail and no other email programs.Does anyone have any solutions??

Well, I did and I didn't.  It's working now and has been for some time, but I'm not really sure why.  I got it working here by fiddling the sections on the server setup, trying different combinations of things like [EMAIL="username@domain.net"]username@domain.net[/EMAIL], username and so on, and fiddling with the settings for security and passwords.  Talk to your ISP and see if that'll help.  Also check with the ISP that you have the right ports set.

As I said I got it working, then we went to Germany, where it immediately stopped working.  I fiddled the [EMAIL="username@domain.net"]username@domain.net[/EMAIL] options and got it working again.  Then we went to France, where it stopped working and I never could get it going again, no matter where we went, so I gave up in disgust.  We returned to the US where the same settings as in France worked just fine.  Then we came home and it stopped working again.  It would work when I first fired the computer up, then quit and I couldn't get it going again.  I took it to our ISP's facility and logged into their wireless there and everything started working fine and has been fine ever since (knock wood), which is about a month now.  There's something about Thunderbird under Ubuntu that my ISP apparently doesn't like, although they claim lots of their users use Thunderbird without problem. :confused:

So, I'm no help, I know, but I can at least offer the encouragement that if you keep screwing with it, you'll probably get it going.  

Good luck

---

