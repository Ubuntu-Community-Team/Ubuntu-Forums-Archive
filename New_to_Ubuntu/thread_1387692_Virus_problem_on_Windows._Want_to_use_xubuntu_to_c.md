---
title: "Virus problem on Windows. Want to use xubuntu to clean."
date: 2010-01-22
forum: New to Ubuntu
---

### Post by aimpau on 2010-01-22
/rant

My parents computer was infected today by a virus/worm/trojan/malware called msmxeng.exe. Now, I tried cleaning it with the antiv and antispy programs installed but they can't do anything. Next, I've searched almost all search engines including infoseek and lycos about removing said virus, either with a program or manually, and all I get are programs that "supposedly" remove the virus though guaranteed removal includes some "monetary" exchange. What the?

So what I did is that I scour the registry of the WinXp and found the filename in one of the keys and deleted it. However, it is still recreating the folder it. No sight of the file in taskmon and c:\>. I can't even delete the folder.

So my solution is pretty simple. Get my liveCD of Ubuntu 8.10 or Xubuntu 7.10 and delete the folder. Re-search said file and delete even more.

/end_rant

Is there an antivirus/antispyware/antimalware/antibad_file program in ubuntu that I can use to scan a Windows partition? I am really getting annoyed with these malwares since almost a lot of them are DOS files that hinder my network connection.

edit:
BTW, for some reason of stupidity, I actually typed command in Run and started typing sudo when it hit me in the head....

edit 2:
**strange, the thread title is actually being chosen or intelligently autocompleting? since I never placed in that title**

---

### Post by Perfect Storm on 2010-01-22
Nah, it's me that edited the title so you can get the right help by the right people more efficient ;)

---

### Post by aimpau on 2010-01-22
Now, that's real time! Thanks!

---

### Post by KeLa on 2010-01-22
There is Avast Antivirus for linux. Just google it.

---

### Post by aimpau on 2010-01-22
I'm actually aware of it but it is used mainly as an email server scanner.

---

### Post by Perfect Storm on 2010-01-22
There's Fprot and AVG also.

---

### Post by aimpau on 2010-01-22
here's a funny thing. I downloaded a program to scan windows. I'm also running two other antispy and antivi in the background, each time the program detects an infected file, the other two detects it as well...wow...

---

### Post by 3rdalbum on 2010-01-22
> **aimpau said:**
> here's a funny thing. I downloaded a program to scan windows. I'm also running two other antispy and antivi in the background, each time the program detects an infected file, the other two detects it as well...wow...

Don't run multiple anti-* programs simultaneously, they can step on eachother's toes. The reason why they all detect the infected file at the same time is because every time any program accesses the file, it gets scanned by any active anti-virus programs.

So, one anti-virus program accesses the file to determine if it has a virus in it, and the act of accessing the file causes the other two programs to check it as well.

---

### Post by aimpau on 2010-01-22
> **3rdalbum said:**
> Don't run multiple anti-* programs simultaneously, they can step on eachother's toes. The reason why they all detect the infected file at the same time is because every time any program accesses the file, it gets scanned by any active anti-virus programs.

So, one anti-virus program accesses the file to determine if it has a virus in it, and the act of accessing the file causes the other two programs to check it as well.

the other two are on "real-time" protection mode which obviously wasn't doing their "real-timeness".... anyways, fixed the problem already. :)

---

### Post by cascade9 on 2010-01-22
> **3rdalbum said:**
> Don't run multiple anti-* programs simultaneously, they can step on eachother's toes. The reason why they all detect the infected file at the same time is because every time any program accesses the file, it gets scanned by any active anti-virus programs.

So, one anti-virus program accesses the file to determine if it has a virus in it, and the act of accessing the file causes the other two programs to check it as well.

+1, Its a bad idea to run multipule anti-virus (or firewalls for that matter).

> **aimpau said:**
> My parents computer was infected today by a virus/worm/trojan/malware called msmxeng.exe. Now, I tried cleaning it with the antiv and antispy programs installed but they can't do anything. Next, I've searched almost all search engines including infoseek and lycos about removing said virus, either with a program or manually, and all I get are programs that "supposedly" remove the virus though guaranteed removal includes some "monetary" exchange. What the?

So what I did is that I scour the registry of the WinXp and found the filename in one of the keys and deleted it. However, it is still recreating the folder it. No sight of the file in taskmon and c:\>. I can't even delete the folder.

So my solution is pretty simple. Get my liveCD of Ubuntu 8.10 or Xubuntu 7.10 and delete the folder. Re-search said file and delete even more.


There are a _ton_ of free anti-virus, anti-spyware, anti-malware etc programs for windows. A lot of them are even good :). As for the virus removal from a search engine...yeah, what did you expect? They will all take money in return for 'bumping' results in a search, so of course your getting the paid for stuff at the top. 

Just deleting the filename probably wont work. You've still got the virus/trojan that is creating the folder. Yes, I know, lots of people remove viruses from windows using linux distros, but IMO its more of a pain than its worth sometimes. 

I'd actually try something like hijackthis. Great little program, finds lots of junk that I've seen other tools miss. Or you could try doing it the long way (which isnt fast, but is very through). See here-

[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

---

### Post by nerdy_kid on 2010-01-22
maybe you can find something here: [http://free.avg.com/ww-en/virus-removal](http://free.avg.com/ww-en/virus-removal)

---

### Post by HarrisonNapper on 2010-01-22
If it is embedded in the registry, it might be better to use a native executable rather than scan from *nix. Avast was suggested earlier and that has boot scan for rootkit detection, but there's also a set of free tools that trend micro offers on their website. HouseCall 7.1 is pretty good ([http://housecall.trendmicro.com](http://housecall.trendmicro.com)) and they have other tools accessible through the sidebar on the left like Rootkit Buster that might help.

---

### Post by ubunterooster on 2010-01-22
I just typed "Virus scanner" into synaptic and installed program of same name. For a liveCD that checks for viruses, though I'd (and have) use Knoppix

---

