---
title: "firefox/opera problem- randomly 'redirecting' me"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by selablad on 2009-04-12
Sorry about the vague title, I'm not sure how to describe the problem succinctly...

Basically the problem is this: every now and then I will try to go to a website, but instead of the actual page loading, there'll just be a white screen with the words 'I am alive!' in the top left corner.  The URL is what it's supposed to be, it's just the page itself that doesn't show.  Refreshing doesn't help, and the same thing occurs in opera and firefox.  If I come back later and try again, the actual page loads normally.  This behaviour is completely random and unpredictable, and very annoying!

Although 'I am alive!' is the most common, sometimes it shows a different page, like google or facebook or something I use often.  But I think this is a different problem as the URL then reads [www.google.com/thepageIwant](www.google.com/thepageIwant), which of course doesn't exist so it gives a 404 error.  Again, I have no idea what's happening!

I'm a bit of a Linux newbie, so any help would be appreciated...

---

### Post by ghostofzuul on 2009-04-12
my first guess would be it's the page you're hitting redirecting you... and it has nothing to do with the browser... the site may have been hacked.

---

### Post by cariboo on 2009-04-12
Is this one particular web site you have the problem with, or is it several?

Jim

---

### Post by pastalavista on 2009-04-12
Why don't you post the actual URL of the site? Is it porn? Does the page load ok in IE or any other OS or other computer?

---

### Post by selablad on 2009-04-12
No, it's several.  It's definitely not the site being hacked, because I can go onto the site on my other computer (Windows Vista something-or-other) without any problems.

I should probably explain a bit more, my laptop (ubuntu intrepid) uses wireless, but the main computer connects directly to the internet.  Uh, my sister's laptop is also Vista and she never has any problems, which leads me to think that it has something to do with ubuntu or linux or something about my personal setup... maybe?

thanks for replying so quickly, by the way :)

edit - no porn, thank goodness :)
The URL doesn't show.  It doesn't properly redirect me, it shows the URL as whatever I typed in, but all it says on the actual page is 'I am alive!' or whatever.

---

### Post by Jazzy_Jeff on 2009-04-12
Maybe your computer has come to life...hehe. :)

---

### Post by aaamos on 2009-04-27
Just to confirm you're not going crazy, selablad, I get exactly the same error. I connect via WiFi to my wireless LAN router, and randomly get the "I am alive!" message, or redirected to a page in the incorrect domain (usually google), which results in a google 404. This happens in both my browsers, Firefox and Opera, and doesn't seem to be linked to specific sites, at least not that I've noticed.

Viewing the source of the page, it's simply the text "I am alive!", no doctype, markup, or anything else.

Very strange - I'd suspect something is wrong with the combination of the http protocol on my Ubuntu machine and my wireless card (Broadcom STA), as I've never encountered this running win32.

---

### Post by straki on 2009-09-07
I have exactly the same problem, "I am alive" shows up instead of, say, the gmail webpage (and others). Switching the browser doesn't help. 

It hasn't appeared in the last 3 months when I was overseas. 

My roommate is on the same wireless connection with a windows laptop, he can view the webpages while I can't.

Can anybody make sure this is not a virus/worm/trojan?

thank you, anyone...

---

### Post by misfitpierce on 2009-09-08
When it redirects you to this page can you right click the page and hit view page info and see if it gives you the actual link of where exactly its taking you?

Also... you are not running through a proxy of any sort are you? Check gnome proxy settings and firefox or other browser settings under network tab to make sure set to no proxy...

---

### Post by mikewhatever on 2009-09-08
Can someone please post a URL.

---

### Post by straki on 2009-09-08
Firefox settings had "Use system proxy settings" checked, I've changed it to no proxies now.

I've restarted firefox, typed [www.gmail.com](www.gmail.com) in the address bar, AFAIK I was directed to [http://mail.google.com/mail/](http://mail.google.com/mail/) and the screen shows the "I am alive!" page. I have the page info output here, what exactly did you want to know, misfitpierce?

Disconnecting and connecting to my wireless network seemed to help, also with Opera. 

If turning off proxies was the solution, I'm happy... but why it says "I am alive!" is still a mystery to me. And the same stuff happened with Opera, which has always had proxies turned off, afaik.

Should it happen again I'll post again... thanks misfitpierce

---

### Post by pastalavista on 2009-09-08
Could you post a screenshot of that next time it happens?

---

### Post by straki on 2009-09-08
Here are the screenshots, and the page info. Sorry for it being in German, I hope you can still guess the meaning.

---

### Post by oboedad55 on 2009-09-08
> **straki said:**
> Here are the screenshots, and the page info. Sorry for it being in German, I hope you can still guess the meaning.

Oh how strange! That first screen is odd, the rest I can't read. Sorry, I failed German in college...

---

### Post by straki on 2009-09-08
Don't worry about the page info window, it is exactly the same as it shows up when the gmail page is loaded correctly, except that there are no "feeds" and "media" tabs...

:confused:

---

### Post by FreewheelinFrank on 2009-09-08
Looks like a router hack.

Reset router (should be a little button you need to press with a pencil tip or similar.)

SET A STRONG PASSWORD.

Flush DNS cache if applicable.

[http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html](http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html)

IMPORTANT: Do this with all Windows machines on the network switched off.

Scan Windows with these programs. You're looking for a DNS changer Trojan which hacks your router.

[SUPERAntiSpyware Free](http://www.superantispyware.com/)
[Malwarebytes' Anti-Malware](http://www.malwarebytes.org/)

Download, install and update the programs.
Always select the option to quarantine any malware found rather than delete it, then you will be able to restore files or registry entries wrongly identified as malware- a rare but not unknown event for any malware scanner.

Also make sure all "sisters/room-mates" running Windows have a good free anti-virus installed. avast!, Antivir and AVG all do free versions.

---

### Post by straki on 2009-09-09
Thanks FreewheelinFrank I did reset the router password and flushed the DNS cache.

And there are no more windows machines in our network anymore :-)

If "it" is still alive, I'll let you all know...

thanks for all your help

---

### Post by zipperback on 2009-09-09
For everyone who has had this problem happen, could you please post a list of what add-ons / extensions you might have installed in your browser? Perhaps there is a questionable plugin that is in the community. I know that a short time ago there was a developer who released a firefox plug which did some unethical things like disabled adblocker plus and some other things too I believe. Perhaps if we can find out what you all have in common with your browsers then perhaps we can track down the problem a little better.

- Zipperback
:popcorn:

---

### Post by Arup on 2009-09-09
Have you tried changing your DNS server to one from Open DNS? It maybe that your ISP's DNS servers are having some issues. Open DNS servers are 208.67.222.222 and 208.67.220.220

---

### Post by straki on 2009-09-09
Zipperback, I've only been using opera with no extensions on it, for a while, and when I was using firefox I only had the flashblock 1.3.12a1 plugin.

I wouldn't be surprised if Arup is right. We have been changing router passwords (involuntarily) several times, and the only provider where this happens to me is iinet in Australia. How do I change to open DNS servers?

And... has actually anybody wondered about the words "I am alive!" themselves... it sounds to me like some kid is having fun sending out this message and reading about it on forums like this all over the world. What do you guys think?

---

### Post by sports fan Matt on 2009-09-09
Here are instructions on OpenDNS and Ubuntu: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

And anything is possible, espicially with the power of the internet.

---

### Post by FreewheelinFrank on 2009-09-09
> **straki said:**
> Zipperback, I've only been using opera with no extensions on it, for a while, and when I was using firefox I only had the flashblock 1.3.12a1 plugin.

I wouldn't be surprised if Arup is right. We have been changing router passwords (involuntarily) several times, and the only provider where this happens to me is iinet in Australia. How do I change to open DNS servers?

And... has actually anybody wondered about the words "I am alive!" themselves... it sounds to me like some kid is having fun sending out this message and reading about it on forums like this all over the world. What do you guys think?

A DNS hijack will send your request for 'gmail.com' to the bad guys' proxy server (probably in the Ukraine somewhere) which will then send you the gmail site plus the ads the bad guys want you to see- probably some links to scam anti-virus programs or browser exploits.

The page you receive will look like the Gmail site but the bad guys can add anything they want. Same goes for any site.

I don't think they'd be much interested in having fun. The message could well be caused by an error in the bad guys' network. It seems to be a message passed around a network from router to router.

[http://en.citizendium.org/wiki/Virtual_Router_Redundancy_Protocol](http://en.citizendium.org/wiki/Virtual_Router_Redundancy_Protocol)

Instead of passing you the gmail.com page, the proxy network has forwarded a router message to you. At least, this is my best guess.

---

### Post by Andrew_Grant on 2009-09-10
I have had the same problem, especially with Opera. The key thing I have found to do, is to switch Opera Turbo to enable, regardless of whether you need it or not, then hit reload or press 'Ctrl+R'. 
Whilst not the best solution it does seem to work.
The cause, at least on cursory glance, appears to be in the operawrapper, I'm not sure if this is being spoofed or not.
Hope this helps.
:)

---

### Post by FreewheelinFrank on 2009-09-10
> **Andrew_Grant said:**
> I have had the same problem, especially with Opera. The key thing I have found to do, is to switch Opera Turbo to enable, regardless of whether you need it or not, then hit reload or press 'Ctrl+R'. 
Whilst not the best solution it does seem to work.
The cause, at least on cursory glance, appears to be in the operawrapper, I'm not sure if this is being spoofed or not.
Hope this helps.
:)

Do you have a router?

Have you tried reseting it?

Does it have a strong password?

Any Windows computers on the same network that could have a DNSChanger Trojan?

[http://blog.washingtonpost.com/securityfix/2008/06/malware_silently_alters_wirele_1.html](http://blog.washingtonpost.com/securityfix/2008/06/malware_silently_alters_wirele_1.html)

---

### Post by Andrew_Grant on 2009-09-11
Thank you. Yes, there are number of Windows computers on my network, some with Me, XP and Vista. Checked them all-as best as I could, reset the router - despite the protestations of my ISP (Verizon for all you in the NY area - they did threaten to charge me), and have run ClamAv on all the Linux computers.
Nothing picked up but am going to keep a good eye on it all.
But thank you again, the link to the Washington Post. Very interesting.:D

---

### Post by Andrew_Grant on 2009-09-11
Very interesting video about removing dns changer(s) from Windows computers here: [http://www.videosurf.com/video/how-to-remove-the-trojan-dnschanger-virus-68524656?vlt=ffext](http://www.videosurf.com/video/how-to-remove-the-trojan-dnschanger-virus-68524656?vlt=ffext)

---

### Post by qamelian on 2009-09-11
> **straki said:**
>  And... has actually anybody wondered about the words "I am alive!" themselves... it sounds to me like some kid is having fun sending out this message and reading about it on forums like this all over the world. What do you guys think?
You don't happen to have a PS3 connected to the router, do you?
[http://portforward.com/english/routers/port_forwarding/Dlink/DSL-504v2/PS3_I_Am_Alive.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DSL-504v2/PS3_I_Am_Alive.htm)

---

### Post by panzerdragoon on 2009-10-24
I'm having the same problems now with my system. I have a netbook running Karmic and a Windows Vista machine. Both are connected wirelessly to the web. My Windows machine seems to be running fine, but my Linux machine constantly acts up when I'm surfing the web. Many of the links I click on in Google Reader direct me to sites like Amazon rather than the intended site, and I often get the "I'm Alive" page too.

I thought that it might be Karmic that's causing the trouble and I was considering getting Windows 7 to install on my netbook, but I'll try some of the tips mentioned here and see if they work.

(I actually posted this problem in another thread and thought I found the solution, but apparently, I hadn't.)

---

### Post by beenhackedtoo on 2010-01-10
I'm having the exact same problem, usually just after I boot up.  It happens with both Opera and Firefox.  I get a white screen with the words "I am alive!", and when I check the page source, it says "I am alive!" there also.

I'm not on wireless.

I'm wondering if we have something else in common, though.  Have you installed Windows 7?

I haven't, but my brother recently installed it on a machine on the same router.  It's a shot in the dark, I know, but stranger things have happened.

---

### Post by beenhackedtoo on 2010-01-10
I noticed someone asked for screenshots. I have them, I'm just not sure how to upload them.  They're 976 kb each, and were taking forever to upload, so I closed the window and they didn't show up.

---

### Post by TBABill on 2010-01-11
I have not been able to find a solution through searching online, but this appears to be a problem others have reported in Windows, Mac and Linux, mostly via Firefox. I did find there was a flash plugin for Firefox that was not actually Adobe Flash. It was a spoof that caused redirect problems and such. I would suggest uninstalling Firefox and reinstalling it fresh without any addons - and do so via the repository. Perhaps a clean install will help if the problem is within Firefox itself. 
 
If Opera uses Firefox settings that may be why they both act in a similar fashion, but I am uncertain whether it does or not. Sorry I can't help more, but not a lot of information is available regarding the "I am alive" redirect that I could find quickly.

---

### Post by TBABill on 2010-01-11
EDIT: The informaiton below was related to MS Word documents, not browsers, but the action sounds very similar with the "I am alive" action. I have not found any link to a web-enabled version of this via browser (checked Symantec, Mcafee and TrendMicro), but it sounds as though it could be an enhanced variant (but that's just opinion)...END EDIT
 
This information is directly from the SYMANTEC website.
If you have this problem then your browser/machine is likely infected. This is a macro-based virus and, according to the website, only affected Windows machines running MS Word, but it appears to be the same or similar based on the explanations of the OP. Possibly this is a copy/derivative of the original? I am not sure, but here's what I was able to find on it. Perhaps a more in-depth search through the other anti-virus sites would provide further answers or newer information.
 
**Discovered: **July 23, 1996
**Updated: **February 13, 2007 11:53:42 AM
**Also Known As: **Polite, Macro.Word.Polite [AVP], WM/Polite [NAI], WM_POLITE [Trend], WM/Polite [Sophos]
**Type: **Macro
**Systems Affected: **Windows 2000, Windows 95, Windows 98, Windows Me, Windows NT, Windows XP
 
 
WM.Polite consists of two macros. 
The first macro is triggered as files are closed. This macro will infect the global template, Normal.dot, unless it already contains the macro module "FileClose." Before it infects Normal.dot, it displays this message: 
I am alive! 
The second macro module is executed as files are saved. This module infects the active document. Before attempting to infect the document, it displays this message: 
Shall I infect the file ? 
If you click No, the file will not be infected. Otherwise, this virus will copy itself into the active document. 
**Recommendations**
 

Symantec Security Response encourages all users and administrators to adhere to the following basic security "best practices":
[LIST]
[*]Use a firewall to block all incoming connections from the Internet to services that should not be publicly available. By default, you should deny all incoming connections and only allow services you explicitly want to offer to the outside world.
[*]Enforce a password policy. Complex passwords make it difficult to crack password files on compromised computers. This helps to prevent or limit damage when a computer is compromised.
[*]Ensure that programs and users of the computer use the lowest level of privileges necessary to complete a task. When prompted for a root or UAC password, ensure that the program asking for administration-level access is a legitimate application.
[*]Disable AutoPlay to prevent the automatic launching of executable files on network and removable drives, and disconnect the drives when not required. If write access is not required, enable read-only mode if the option is available.
[*]Turn off file sharing if not needed. If file sharing is required, use ACLs and password protection to limit access. Disable anonymous access to shared folders. Grant access only to user accounts with strong passwords to folders that must be shared.
[*]Turn off and remove unnecessary services. By default, many operating systems install auxiliary services that are not critical. These services are avenues of attack. If they are removed, threats have less avenues of attack.
[*]If a threat exploits one or more network services, disable, or block access to, those services until a patch is applied.
[*]Always keep your patch levels up-to-date, especially on computers that host public services and are accessible through the firewall, such as HTTP, FTP, mail, and DNS services.
[*]Configure your email server to block or remove email that contains file attachments that are commonly used to spread threats, such as .vbs, .bat, .exe, .pif and .scr files.
[*]Isolate compromised computers quickly to prevent threats from spreading further. Perform a forensic analysis and restore the computers using trusted media.
[*]Train employees not to open attachments unless they are expecting them. Also, do not execute software that is downloaded from the Internet unless it has been scanned for viruses. Simply visiting a compromised Web site can cause infection if certain browser vulnerabilities are not patched.
[*]If Bluetooth is not required for mobile devices, it should be turned off. If you require its use, ensure that the device's visibility is set to "Hidden" so that it cannot be scanned by other Bluetooth devices. If device pairing must be used, ensure that all devices are set to "Unauthorized", requiring authorization for each connection request. Do not accept applications that are unsigned or sent from unknown sources.
[*]For further information on the terms used in this document, please refer to the [Security Response glossary]("http://www.symantec.com/business/security_response/glossary.jsp").
[/LIST]**Writeup By: **Neal Hindocha

---

### Post by TBABill on 2010-01-11
Ok, third post in a row on this one. I have tunnel vision for problems like the OP posted. I focused on "I am alive" and I think that made the search ineffective online. However, if you do a search for Google redirect virus you will see many postings. What I cannot find is anything that points directly to Linux distributions yet. However, it seems to span across operating systems and the key links are Opera and Firefox. I have to get back to work but hopefully someone can continue the search to see if the Linux versions of Opera and Firefox are actually susceptible, and how they are susceptible, to the virus if that's found to be the cause.
 
It looked like people on Windows who were infected had a great deal of difficulty eliminating all traces of it so hopefully it is not a similar problem on Linux machines. It shouldn't be since we have a very different security configuration than Windows, but maybe something happened on some machines while operating as root?
 
Any follow-on help figuring this one out could be huge. It appears many of those were infected through Facebook and MySpace.

---

### Post by J V on 2010-01-11
Oh for the millionth time, *there are no linux virusses in the wild*

If it is malware its a firefox exploit, one which is probably unfixable seeing as its been around so long- And its probably because the site you are looking at (As mentioned before, also, probably running on windows) has been hacked...

---

### Post by TBABill on 2010-01-11
Sorry, I did not intend to imply that anyone on a Linux distro may have a virus. I was pointing out that there are viruses in the Windows world that this problem seems to mimic in some ways (most likely just malware). However, spyware/malware/virus are all concerning and the OP was looking for assistance finding and clearing the problem. I found what I could with my skills, time and focus, but there is obviously a minor infection of some sort that is still outstanding and any assistance pointing to an exact cause and remedy are appreciated. My machine is not suffering from these problems, but I hope the OP finds a solution and will share with everyone for future reference and searches of the forum.

---

### Post by twinaxel on 2010-01-11
Some more info [http://www.bleepingcomputer.com/forums/lofiversion/index.php/t268735.html](http://www.bleepingcomputer.com/forums/lofiversion/index.php/t268735.html)

---

### Post by aaamos on 2010-03-27
It's nearly a year since my last post, and I came across this thread again by chance while searching for something else. Since I haven't encountered this problem for ages, I wondered what may have "fixed" the issue (or at least made it disappear). Reading, through some of the other posts, I remembered that I'd got a new router ages ago, which makes me wonder whether it could've been a sort of "virus" in my router. Was anyone else who encountered this problem using a D-Link router?

---

### Post by Helkaluin on 2010-03-27
Should've been some old exploit (possibly on the router, possible a trojan on the Windows machines in the network) that carries out a DNS spoof attack.

---

### Post by krisgesling on 2010-05-30
So it turns out my compty was just toying with me, making me think that it was fixed and the problem has returned.

<PERHAPS NOT>
Hey I just had this problem and fixed it by defining the DNS servers on my router rather than letting it automatically detect them.

Strange thing is I've been using the same modem (D-Link DSL-G604T) with the same ISP for ages but I updated the firmware yesterday so it must be a bug in that I guess. Either way its all working fine now.
</PERHAPS NOT>

---

### Post by krisgesling on 2010-05-30
It might be related to my proxy settings which I have set up for uni.

The problem stopped immediately when I changed firefox to use no proxy but when switching it back didn't start happening again so maybe its completely unrelated and just another red herring

Pretty frustrating

---

### Post by jrodimusprime on 2010-06-05
Try disable ipv6.

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

Also clear cache and clear dns cache in FF.

---

