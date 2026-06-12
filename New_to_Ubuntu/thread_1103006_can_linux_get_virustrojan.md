---
title: "can linux get virus/trojan??"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by enri2 on 2009-03-22
and from what files can you get it from?

---

### Post by PatrickMoore on 2009-03-22
of course linux can, however it is much more unlikely as viruses are typically written for windows.

---

### Post by mlentink on 2009-03-22
There are numerous threads about this issue, seems to be the primary concern of many (ex-?) windows users.
For all practical purposes, you don't need to worry about viruses. The only way you could get one is if you deliberately installed it yourself. And then it could not propagate, because other users would not allow it to be installed on their system. Basically, the same hold for trojans.

---

### Post by LiamWilson on 2009-03-22
Not so much trojans, but there are a couple of viruses that are out there for Linux, but they don't usually do much, becuase you need to enter your password to do main things, such as mess about with your system files.

---

### Post by mvalviar on 2009-03-22
You'd have to be uber careless to be bothered by one.

---

### Post by LowSky on 2009-03-22
> **LiamWilson said:**
> Not so much trojans, but there are a couple of viruses that are out there for Linux, but they don't usually do much, becuase you need to enter your password to do main things, such as mess about with your system files.

Name just ONE Virus!

None exist in the WILD

---

### Post by Dan_Dranath999 on 2009-03-22
from: [URL="http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/"]http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/

[/URL]
According to Dr. Nic Peeling and Dr Julian Satchell's [Analysis of the Impact of Open Source Software ]("http://www.govtalk.gov.uk/documents/QinetiQ_OSS_rep.pdf")(note: the link is to a 135 kb PDF file):

"There are about 60,000 viruses known for Windows, 40 or so for the Macintosh, about 5 for commercial Unix versions, and perhaps 40 for Linux. Most of the Windows viruses are not important, but many hundreds have caused widespread damage. Two or three of the Macintosh viruses were widespread enough to be of importance. None of the Unix or Linux viruses became widespread - most were confined to the laboratory."

---

### Post by enri2 on 2009-03-22
> **Dan_Dranath999 said:**
> from: [URL="http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/"]http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/

[/URL]
According to Dr. Nic Peeling and Dr Julian Satchell's [Analysis of the Impact of Open Source Software ]("http://www.govtalk.gov.uk/documents/QinetiQ_OSS_rep.pdf")(note: the link is to a 135 kb PDF file):

"There are about 60,000 viruses known for Windows, 40 or so for the Macintosh, about 5 for commercial Unix versions, and perhaps 40 for Linux. Most of the Windows viruses are not important, but many hundreds have caused widespread damage. Two or three of the Macintosh viruses were widespread enough to be of importance. None of the Unix or Linux viruses became widespread - most were confined to the laboratory."

thanks:D

---

### Post by davo11 on 2009-03-22
yes, but because of the way linux is structured it cannot spread very easily.
since many files in linux are owned by root and are read only by other users the virus cannot do anything to these files unless it is acting as root.
the viruses are out there but, unless you're [I]very[I] careless, then they won't affect your system badly.

---

### Post by enri2 on 2009-03-22
> **davo11 said:**
> yes, but because of the way linux is structured it cannot spread very easily.
since many files in linux are owned by root and are read only by other users the virus cannot do anything to these files unless it is acting as root.
the viruses are out there but, unless you're [I]very[I] careless, then they won't affect your system badly.

thanks. I didn't have antivrus in windows so  I think I had some viruses.

---

### Post by mlentink on 2009-03-22
> **enri2 said:**
> thanks. I didn't have antivrus in windows so  I think I had some viruses.
 
In windows, that's a probability approaching 1

---

### Post by dacorr on 2009-03-22
True there are limited viruses for linux and due to how linux operates it would only ever be able to affect a component. However that said the most likely problem would be web browser based annoyances as Firefox runs on both platforms. i believe it would be more likly that this would be the closest thing to a linux virus unless it becomes specifically targeted.

---

### Post by InfectedWithDrew on 2009-03-22
There is a virus scanner called ClamAV for Linux and while you don't *need* it, it's nice to have for scanning Windows systems and flash drives.  Make sure to run it with gksudo after installing it.

----------------
Now playing: [tobyMac - Burn For You (Math Remix)](http://www.foxytunes.com/artist/tobymac/track/burn+for+you+(math+remix))

---

### Post by dacorr on 2009-03-22
f-prot works better (command line based), there is panda also but i belive that is paid for.

---

### Post by philinux on 2009-03-22
The point people always make about root is misleading. If someone where to write a virus for linux they would target the home directory as that is where stuff like banking details etc might be found.

---

### Post by rickandsuch on 2009-03-22
> **philinux said:**
> The point people always make about root is misleading. If someone where to write a virus for linux they would target the home directory as that is where stuff like banking details etc might be found.

Good point, but can't you encrypt home directory files and password protect them as well?

---

### Post by dacorr on 2009-03-22
encyption would not work as it is decrypted for you to access it, there for any virus would have access to it while you are logged in.

a Simple solution is to create encrypted volumes using trucrypt and store sensitive data in them, i have about 3, 200MB, 4GB and 12GB no problems so far.

Dac

---

### Post by elliotn on 2009-03-22
Well I see there is a Avast antivirus for Linux, and also wondered why, well avast is preparing for the future

---

### Post by JK3mp on 2009-03-22
In order to decrypt it it would have to have to be a Trojan not a virus, as far as allowing the owner of the trojan to view the files and it would still need a full connection to your comp which would require root correct? That or vast stupidity from the user...

---

### Post by dacorr on 2009-03-22
> **JK3mp said:**
> In order to decrypt it it would have to have to be a Trojan not a virus, as far as allowing the owner of the trojan to view the files and it would still need a full connection to your comp which would require root correct? That or vast stupidity from the user...

The trojan would not need to as the user would need to inorder to login and use the account, if it operated from the home directory itself then it too would be encrypted. Bearing in mid theoretically we were considering that user based viruses would be more likly then ones targeting root processes.

in order for that the user would need to be running somthing themselves or had user input, but alot of viruses/malicous apps rely on social engineering.

Encryption is only part of a security policy and should be used in conjuction with other securty measures. If the machine is stolen then encryption would help. alot of trojans are designed to obtain information from the user while using their machine.

Potentially what ever i have access to malicouse software could also.

Bearing in mind i am more paranoid than normal

Dac

---

### Post by gn2 on 2009-03-22
> **elliotn said:**
> Well I see there is a Avast antivirus for Linux, and also wondered why, ~

So that you can scan files destined for Windows computers.

Which is (currently) the only reason to use anti-virus on a Linux operating system.

---

### Post by presence1960 on 2009-03-22
to see the difference between windows security & linux read this : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

now you decide!

---

### Post by presence1960 on 2009-03-22
> **elliotn said:**
> Well I see there is a Avast antivirus for Linux, and also wondered why, well avast is preparing for the future

I may be incorrect so correct me if I am. But I believe Avast scans only for Windows based viruses. There's no future in that !

---

### Post by lisati on 2009-03-22
The best starting place for protection against viruses, trojans, worms, and malware in general is using a modicum of good sense, e.g. exercise caution before opening attachments or following links from people you don't know.

I probably don't need to point out that the thing about trojans is that the malicious software often comes disguised as something potentially useful.

---

### Post by llamabr on 2009-03-22
From my perspective, you're unlikely to get a virus for a few reasons.  First, viruses are written to infect MS windows.  The same reason any other .exe file won't work keeps viruses from working.

Next, the permissions structure would keep a virus from doing any real damage on your system anyway.

Finally, there is some malware that will infect your system if you're running a mail server, a blog or wiki, and some web applications.

---

### Post by gimmejimmy on 2009-03-22
I read an interesting article some months back:
[http://http://www.geekzone.co.nz/foobar/6229]("http://http://www.geekzone.co.nz/foobar/6229")
And its follow-up:
[http://www.geekzone.co.nz/foobar/6236]("http://www.geekzone.co.nz/foobar/6236")
It's interesting reading.  Linux is much safer than Windows, but we shouldn't be smug about it.  Common-sense still applies.  It's very, very unlikely but not impossible to get malware, and it won't need root access to hurt you.

---

### Post by linuxrollup on 2009-03-22
Linux is structured in such a way that nasties can't spread easily. (Ex) Windows users tend to worry about this but Linux is constantly updated by the community and with them behind you, it's not really an issue.

---

