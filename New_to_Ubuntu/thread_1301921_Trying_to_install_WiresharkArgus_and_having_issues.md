---
title: "Trying to install Wireshark/Argus and having issues"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Kayone on 2009-10-26
[COLOR=Red][B][COLOR=Black]First off, I would like to thank anyone who helps. I am about as slow as they come so you're assistance is going to be greatly appreciated. My level of experience would probably be at your 8 year olds level :)

So. I am trying to install Wireshark and Argus.  I want to set Wireshark's live capture (promiscuous mode) and then use Argus to parse the data. I would like to eventually output that data into an SQL database so I can query the netflow (or use it to identify false positives). Sadly, I am use to point and click with Windows.  

Please remember, I need specfics. If you ever said there was no such thing as a stupid question, be preparred to be proven wrong ~LOL 

1. My comprehension of a respoitory is limited. I know I can click on "Applications -> Add/remove Programs" to add on tools. I managed to install Wireshark but I am unable to set it up properly. I believe my issue is the lack of understanding when setting up an Interface but I am not sure. I just know, when I click on "Capture -> Options", I am not able to see an interface when I click on the drop down menu. "Capture -> Interfaces" doesn't show me any interfaces

2. Libpcap/M4/Bison/Flex...  I am unable to install it (also cannot install bison/flex properly).. I get error messages about "m4-1.4.13".. unfortunately, I have tried to install that as well and I got another error message..  I would like to have a clue what is going on here but I don't know where to start... I feel like I just had a stroke and I am trying to re-learn basic functionality...

me@me-desktop:~/Desktop/libpcap-1.0.0$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking gcc version... 4
checking for inline... inline
checking for __attribute__... yes
checking for u_int8_t using gcc... yes
checking for u_int16_t using gcc... yes
checking for u_int32_t using gcc... yes
checking for u_int64_t using gcc... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGEFILE_SOURCE value needed for large files... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/ioccom.h usability... no
checking sys/ioccom.h presence... no
checking for sys/ioccom.h... no
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for net/pfvar.h... no
checking for netinet/if_ether.h... yes
checking for ANSI ioctl definitions... yes
checking for strerror... yes
checking for strlcpy... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing putmsg... none required
checking for ether_hostton... yes
checking whether ether_hostton is declared... no
checking netinet/ether.h usability... yes
checking netinet/ether.h presence... yes
checking for netinet/ether.h... yes
checking whether ether_hostton is declared... yes
checking if --disable-protochain option is specified... enabled
checking packet capture type... linux
checking Linux kernel version... 2
checking for linux/wireless.h... yes
checking if if_packet.h has tpacket_stats defined... yes
checking if tpacket_auxdata struct has tp_vlan_tci member... no
checking for getifaddrs... yes
checking ifaddrs.h usability... yes
checking ifaddrs.h presence... yes
checking for ifaddrs.h... yes
checking for socklen_t... yes
checking for getaddrinfo... yes
checking whether to build optimizer debugging code... no
checking whether to build parser debugging code... no
checking whether we have /proc/net/dev... yes
checking whether we have DAG API headers... no (/usr/local/include)
checking whether we have the DAG API... no
checking whether we have Septel API... no
checking for flex... no
checking for bison... no
checking for capable lex... insufficient
configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 [http://www.gnu.org/software/flex/flex.html](http://www.gnu.org/software/flex/flex.html) .


More questions to follow!
Thank you in advance!

-k1

[/COLOR] [/B][/COLOR]

---

### Post by Sarmacid on 2009-10-26
For the wireshark issue, seems you're not running it as admin. To do this, open up a terminal and type ```
sudo wireshark
```Input your user's password and see if it works.

As for the other issue, argus-client and argus-server are on the repos, not sure if it's what you want but you should check those out, since installing those would be a lot easier. If you wanna go ahead and compile, you're gonna need flex first. To install this go to system -> Administration -> Synaptic package manager. Go down to flex, right click and mark it for installation, then hit the apply button under the menu bar. You should be able to satisfy that dependency now.

---

### Post by Kayone on 2009-10-26
> **Sarmacid said:**
> For the wireshark issue, seems you're not running it as admin. To do this, open up a terminal and type ```
sudo wireshark
```Input your user's password and see if it works.

As for the other issue, argus-client and argus-server are on the repos, not sure if it's what you want but you should check those out, since installing those would be a lot easier. If you wanna go ahead and compile, you're gonna need flex first. To install this go to system -> Administration -> Synaptic package manager. Go down to flex, right click and mark it for installation, then hit the apply button under the menu bar. You should be able to satisfy that dependency now.

1.. Wireshark does live capture... you rock... I didn't even think about the need for root when you are setting up a sniffer on a computer  ):P Hello common sense, nice to meet you. I do have a question though, I tried to do everything as root via command line. Unfortunately, I didn't try to sudo into Wireshark. If I sudo su, does that only establish root for that cmd.exe session?  (I guess that explains why you can log into superuser from one window and when you open up another command line, you open it up as if you weren't root)...

2. Checking the rest now :) I assume I need to reboot after each instillation?

---

### Post by Sarmacid on 2009-10-26
> **Kayone said:**
> If I sudo su, does that only establish root for that cmd.exe session?
I see you still have some windows in you :P it's a terminal session and yes, you're only root in that terminal. I'd suggest you read this to fully understand it [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Kayone on 2009-10-29
> **Sarmacid said:**
> I see you still have some windows in you :P it's a terminal session and yes, you're only root in that terminal. I'd suggest you read this to fully understand it [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Busted... :popcorn: ... Reading now ...

---

### Post by running_rabbit07 on 2009-10-29
Wow, another Va user. I am from Lynchburg. Not there anymore though.

---

### Post by Kayone on 2009-10-29
Sadly, there wasn't anything I haven't probably read a 100 times at some point. Growing pains I guess :)

I actually prefer when people correct me on terminology. Correct away!

So, who is ready to step up to the Argus challenge?

Wireshark is good. I have everything ready to go (I think).

I am trying to figure out the syntax in Argus to parse PCAP files stored in a directory. I basically want everything logged/reported for now. I think it will be easier to see an extremely verbose dump and shrink it based on my specific needs.

Another question. 

When it comes to the client and server. Is the server designed to go on a box to sniff traffic? I would assume the client would be the only program I would actually need to install?

I normally think "Google it" when people ask dumb questions. Believe me, I have tried. I guess I am either too dumb to read people's technical responses or the answer is so convoluted that I can't see it. Man pages are like reading RFC's sometimes. Once I get the terminology for a tool down, I can learn the ins and outs. Until then, I am left trying to translate a foreign language only to find out that it translates to a document that teaches you to translate another language :D

---

### Post by Kayone on 2009-10-29
> **running_rabbit07 said:**
> Wow, another Va user. I am from Lynchburg. Not there anymore though.

Hey there... I travel quite a bit actually. I have lived everywhere from Stafford to Chesapeake to VA Beach.  Nice to meet you :D  I am actually more from California/Maryland if that makes sense.

---

### Post by Kayone on 2009-10-29
OMFG Rabbit.. Your "Get Help" link is awesome! I just saw that! Clever!

---

### Post by running_rabbit07 on 2009-10-29
> **Kayone said:**
> OMFG Rabbit.. Your "Get Help" link is awesome! I just saw that! Clever!

Lol, Google is the fastest way to find already open help threads in Ubuntu Forums when you need answers.

---

### Post by Kayone on 2009-10-29
> **running_rabbit07 said:**
> Lol, Google is the fastest way to find already open help threads in Ubuntu Forums when you need answers.

You could always make it:  :D

<a href="http://www.google.com/search?hl=en&lr=&q=%22type+your+question+here+and+remove+the+quotes%22+site%3Ahttp%3A%2F%2Fubuntuforums.org&btnG=Search&cts=1256839123087&aq=f&oq=&aqi=" target="_blank">Get Help!</a>

---

### Post by running_rabbit07 on 2009-10-29
> **Kayone said:**
> You could always make it:  :D

<a href="http://www.google.com/search?hl=en&lr=&q=%22type+your+question+here+and+remove+the+quotes%22+site%3Ahttp%3A%2F%2Fubuntuforums.org&btnG=Search&cts=1256839123087&aq=f&oq=&aqi=" target="_blank">Get Help!</a>

That came out as a garbled mess. I always do a search first. In the past I have had people do to me what you talk about in your signature and get stuck trying to figure out why they couldn't type a few more words to just answer my question. Unless someone is getting rude, I usually take the time to explain how to fix their problem if I know how.

The get help link is there just to kinda let newbies know that google is very helpful with finding fixes on Ubuntu. When I first started, I was having massive problems with Debian and had no clue Google could have helped me.

---

### Post by Kayone on 2009-10-29
Haha.. that didn't work. Hmm. I guess I will need to look up how to rename a link.

---

### Post by running_rabbit07 on 2009-10-29
> **Kayone said:**
> Haha.. that didn't work. Hmm. I guess I will need to look up how to rename a link.

Type the word you want to use as a link, highlight it, then click the button in the screenshot to make it a link

---

### Post by Kayone on 2009-10-29
> **running_rabbit07 said:**
> Type the word you want to use as a link, highlight it, then click the button in the screenshot to make it a link

How do you rename it though. Like you would in HTML by adding text in the href tag:
<a href="www.google.com/blah/blah/blah">RENAMED PLACE</a>

---

### Post by Kayone on 2009-10-29
LMAO... I just derailed my own post.

(Sorry Mods.. I'm noob!)

---

### Post by running_rabbit07 on 2009-10-29
> **Kayone said:**
> How do you rename it though. Like you would in HTML by adding text in the href tag:
<a href="www.google.com/blah/blah/blah">RENAMED PLACE</a>

I don't know how to do that.

---

### Post by Kayone on 2009-10-29
How did you make yours say "Get Help" instead of "www.google.com"

---

### Post by running_rabbit07 on 2009-10-29
> **Kayone said:**
> How did you make yours say "Get Help" instead of "www.google.com"

I typed get help, then clicked the link button. Are you using Epiphany or Firefox? Epiphany gave me that problem when trying to make links.

---

### Post by Kayone on 2009-10-30
> **running_rabbit07 said:**
> I typed get help, then clicked the link button. Are you using Epiphany or Firefox? Epiphany gave me that problem when trying to make links.


I am using Firefox :)

I did it finally. I was making that a lot more difficult than necessary (as usual)! 

I tried to "view source" of your page, find your signature in the HTML source, and paste that into my signature. Then I doctored up your URL and made it even easier to use Google to search for answers in the forum. 

Something that was supposed to be hardly funny turned into me laughing at myself because I couldn't figure out the simplest function on here. 

If I can't laugh at myself, I will be the only one in the room not laughing at me :p

---

### Post by Kayone on 2009-10-30
ok... back to the Argus question:

I have read all kinds of confusing explanations out there.


[https://bugs.launchpad.net/ubuntu/+s...us/+bug/192868]("https://bugs.launchpad.net/ubuntu/+source/argus/+bug/192868")

[http://www.linuxquestions.org/questi...-argus-698865/]("http://www.linuxquestions.org/questions/linux-software-2/problem-installing-argus-698865/")

[http://packages.debian.org/lenny/i38...erver/download]("http://packages.debian.org/lenny/i386/argus-server/download")

[http://web.archive.org/web/200801191...s/how-to.htm#3]("http://web.archive.org/web/20080119143705/http://qosient.com/argus/how-to.htm#3")

Nothing is clear to me. Can someone point out what I am supposed to do here.

I am pretty new to Linux (8.04). I have taken a bunch of classes that taught different aspects of the OS but I never dove into it. I probably know some less-than-newb information and totally forgot something about the core functionality of the OS. Please bare with me. This may be painful.

Argus:

I keep reading about people having the same issue getting Argus to work on Linux for them. I hear people saying that this issue doesn't exist on older versions of Argus.

Honestly, I don't care if I need to download the older version. I would rather not but if that is what I need to do, feel free to direct me that way.

Basically, I am trying to run Argus (netflow analyzer) against PCAP data to pull out metadata. I want the output to go to a SQL database.

This seemed like a simple task at first. This isn't necessarily the case anymore.

I have been trying to find a clear cut answer for 2 days now and it is literally beyond me. I tried using the repo's.. I tried sudo apt-get install.. The furthest I got was being able to use man pages for Argus. Unfortunately, when I tried to run a command, it said I didn't have the server running. I tried to uninstall and re-install. Nothing.

If someone could please explain what I need to do, I would be greatly appreciative. I am wasting too much time trying to figure this out on my own and this is too valuable to give up on.

I have been to qosient.com.. maybe I missed what I needed to do.
This isn't as simple as going to a repo. I am kinda sure I downloaded/installed the proper files that Argus needs. I have libpcap, m4, bison, and flex. 

I'm so lost.

---

### Post by Kayone on 2009-11-02
bump :)

---

### Post by Kayone on 2009-11-02
*************** This is where I have gotten so far**************

I have gotten this far since the stuff I posted below. This kinda has the functionality I would like (or at least I think this is what I am going for)

sudo argus -r slammer -w - | ra -n

I mean, I am eventually going to try to get to the point to where this is going to be added to a SQL database (wishful thinking). 

To the best of my understanding, this line is:

sudo: Giving me permissions to run the program

argus: telling the argus program to run

-r: Says it is reading from tcpdump (basically lets it know that slammer is a pcap file that I got from a tcpdump output)

slammer: This is the file I am running argus against. Argus is natively designed to be a promiscuous sniffer and create netflow metadata based on that . Since I already have my collection center running tcpdump, and my primary focus is on the packet data, I didn't want to over burden my sensor. I want to process the data somewhere else. I decided to create netflow data based purely off the packet data so I could see the big picture. Eventually I will use this for other purposes as well. 

-w -: This creates an output file. You will notice that my output file is a dash (-). This makes the output/results of my process print to my screen (stdout). I am only using this for testing purposes. This will definitely change.

************ This is where I have given up at this time************

I am trying to have Argus read PCAP files from a directory. I assume you would only run the argus daemon if you were sniffing traffic live? If that is the case, do I even need to configure anything?

Basically, I want to create a script that will make readable netflow data out of a whole directory full of pcap files. I will want argus to only run when the script is ran.

Also, I gave up on installing the newer version. I just installed from [http://packages.debian.org/lenny/i38...erver/download]("http://packages.debian.org/lenny/i386/argus-server/download"). It appears that this works.

There are a few questions I have though:

argus -r ./packetfile 

When looking at the man pages, it says -r Read from tcpdump(1) , snoop(1) or NLANR’s Moat Time Sequence Header (tsh) packet capture files. If the packet capture file is a tsh format file, then the -t option must also be used. Argus will read from only one input packet file at a time. If the -r option is specified, argus will not put down a listen(2) to support remote access.


[http://web.archive.org/web/200801191...s/how-to.htm#3]("http://web.archive.org/web/20080119143705/http://qosient.com/argus/how-to.htm#3")

When I tried to do this, it kicked back my shell as if it were successful. The problem is, I think this isn't doing what I need it to do (if it is doing anything at all). Maybe I am missing the big picture. 

As a test, I have a pcap file called slammer on my Desktop. I changed directories to my Desktop and then I typed "argus -r ./slammer". 

I am assuming that this is telling argus to keep an eye on that file by running as a persistent daemon? It is keeping the results in virtual memory until I pull out the data through a program like ra?

In theory, I would like to make argus read through a directory of pcap files and output all of the metadata so I could read all of the IP addresses/ports/etc that were associated.

Is there any way I can make argus read the data and output the information in a file that I can read or do I need to run a bunch of separate commands to do that? I don't need to read packets from a network interface.

---

### Post by Kayone on 2009-11-04
This is still where I am still stuck.

sudo argus -r slammer -w - | ra -n

I want to make Argus read the file and output the data to a file. That isn't working the way I would expect. This is what is happening:

sudo argus -r pcapfileiammakingnetflowfrom -w netflowdatafile

This creates a file named netflowdatafile. Even if I manually chmod 777 the file, I still have issues reading it with ra. I am totally confused. The man pages don't really make this so I can understand it and I can't exactly get things to work (otherwise I would try out every option until I got the desired affect).

---

### Post by Kayone on 2009-11-04
I mean, I can type in the commands below to spit it out into a file if I needed to but I am trying to understand the syntax to fully optimize argus. 

argus -r slammer -w - | ra -n -z -L0 > slammer


I guess I am asking why the following doesn't work:

When using Argus:

 -w   <file ["filter"] Write transaction status records to  output-file.
        An  output-file of ’-’ directs argus to write the resulting argus-
        file output to stdout.

**shouldn't this allow me to type "argus -r slammerpcap -w slammerarg" and make argus read the pcap file (called slammer) and then output the results into a file that can be read by ra (called slammerarg)?

When using ra, shouldn't I be able to use it as a text viewer of some sort. Shouldn't I be able to use ra to manipulate the results I am seeing? 

Trying to figure this out is driving me crazy. It isn't doing what I think it should be. Maybe I should try to set this up as an active netflow generator and try to make that work. It seems like that is what most people are using this for.

---

### Post by Kayone on 2009-11-09
I was originally doing the following command to output data to a file because I wasn't able to do it originally (the way I wanted to). Please read further for the explanation. 

Basically, the line below uses the "-r" option to read "pcapfile". I had to use the "-w -" option to output the results to the screen (the - after the -w makes the output go to the screen). 

Remember, I actually wanted to output to a file. I basically found a workaround by:
pcap --> print to screen ---> redirect screen to file named slammer

argus -r pcapfile -w - | ra -n -z -L0 > argusfile


> **Kayone said:**
> 

I guess I am asking why the following doesn't work:

When using Argus:

 -w   <file ["filter"] Write transaction status records to  output-file.
        An  output-file of ’-’ directs argus to write the resulting argus-
        file output to stdout.

**shouldn't this allow me to type "argus -r slammerpcap -w slammerarg" and make argus read the pcap file (called slammer) and then output the results into a file that can be read by ra (called slammerarg)?

When using ra, shouldn't I be able to use it as a text viewer of some sort. Shouldn't I be able to use ra to manipulate the results I am seeing? 

Trying to figure this out is driving me crazy. It isn't doing what I think it should be. Maybe I should try to set this up as an active netflow generator and try to make that work. It seems like that is what most people are using this for.

I feel like a skitzo here.... I am responding to myself. 

Answers to my problems ended up being a long and tedious process. I am not able to read the code of the program well enough to actually figure anything out on my own. I am kinda noob here so, instead of being able to eliminate simple operator errors from troubleshooting, I ended up thinking everything was an issue with my syntax and my unserstanding for the Linux OS.

Having said that, my question was "**shouldn't this allow me to type "argus -r slammerpcap -w slammerarg" and make argus read the pcap file (called slammer) and then output the results into a file that can be read by ra (called slammerarg)?"

The answer is yes!

I want to give you the long version because I ended up making this work (I am unsure what made it work but it only worked a few seemingly-random times). Ultimately, only one thing fixed it, I HAD TO REMOVE THE /ETC/RA.CONF FILE!!!

[http://article.gmane.org/gmane.network.argus/5671](http://article.gmane.org/gmane.network.argus/5671)

I had actually read the above at least 3-4 times before I understood that this was my problem. Unfortunately, I had so many issues along the way that I didn't see this when I actually needed to and then started overlooking it when I did need it!

Basically, the article states that the /etc/ra.conf file was created from the argus 2 install. Some of you may not have had this issue because you didn't install argus 2. If you did, you might want to type in the following command "locate /etc/ra.conf". If you have it, you might want to move it to your desktop and see if that fixes your problem. It surely fixed mine. I moved mine there because I wasn't sure what it would break if I got rid of it. I am still not sure at this time but if Carter said it is good, it must be. 

I hope this helps someone.

I wish I could explain why the repositories didn't work when trying to install. I cannot. I actually had to get a copy from a friend to be able to get that to work. I had to use argus 3. The first attempt to download 3 didn't help me at all. I am probably going to need to re-install this at multiple locations with multiple versions of Linux. If I figure it out, I will keep posting here.

Good luck.

---

