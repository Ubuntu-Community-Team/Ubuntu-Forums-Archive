---
title: "I'm attacked by russian guys - when i visit them , they .  .  ."
date: 2009-07-18
forum: New to Ubuntu
---

### Post by kain1 on 2009-07-18
So when I visit them, -after I offended them once - it's a religious site/blog -  they have initiazed my modem 5 times now
and do other strange things.

They even did this 1 time when I acceded their YOUTUBE page where I was already blocked
The moment I tried to subsribe again it appened
THIS SEEMED ALMOST IMPOSSIBLE TO ME
and mede me think that Google Employees were involved.


So, .  . I cleaned my PC from all text files etc , and even bought 4 Hard Drives
all completely virgin with Ubuntu 9.04 /daily update - NOT automatic ( wow )

Is there a firewall  like BLACKICE for Windows, to better see where it's coming from and how ?

This started on my Windows XP and therefore I changed to Linux.
It seems to me that they know Linux much better than Windows
All symptoms grew worse


Is there a program that put ALL authorizations on "Authorize" with ONE STROKE
like F10 and then F11 fot Default - that would be so nice

Is there software to analyse the Logfiles more automatically

Kain1

---

### Post by Paqman on 2009-07-18
> **kain1 said:**
> So when I visit them, -after I offended them once - it's a religious site/blog -  they have initiazed my modem 5 times now
and do other strange things.


Hi, i'm a bit confused by this. What do you mean when you say "my modem initialised"? Can you be more specific about what the actual problem is?

However, i'd say it's highly unlikely anyone is attacking you. Despite the threats that some people throw around the internet, you can rest assured that the vast majority of people you offend will have no actual way of attacking you. Unless you're trolling on black hat hacking sites, I guess...

> 
They even did this 1 time when I acceded their YOUTUBE page where I was already blocked
The moment I tried to subsribe again it appened
THIS SEEMED ALMOST IMPOSSIBLE TO ME
and mede me think that Google Employees were involved.


I highly doubt Google employees are involved, you're being paranoid.

> 
So, .  . I cleaned my PC from all text files etc , and even bought 4 Hard Drives
all completely virgin with Ubuntu 9.04 /daily update - NOT automatic ( wow )

Is there a firewall  like BLACKICE for Windows, to better see where it's coming from and how ?


Linux comes with a firewall system built in. A good tool for managing it is gufw.

> 
This started on my Windows XP and therefore I changed to Linux.
It seems to me that they know Linux much better than Windows
All symptoms grew worse


That would suggest that the problem is your hardware, but without a better idea of what is happening it's hard to say.

> 
Is there software to analyse the Logfiles more automatically

Kain1

Go to System > Admin > Log file viewer. From there you can go to View > Find and search for what you're interested in.

---

### Post by kerry_s on 2009-07-18
sounds like a hardware issue or he's just a troll, cause it just don't make sense.

---

### Post by 3rdalbum on 2009-07-18
So you're saying that they are tracking you across a change of operating systems and across your (presumably daily) change of IP addresses? And that they're spending all their time hacking into Youtube just to annoy you?

That's highly implausible. The problems with your modem are most likely hardware problems, and getting worse due to your modem getting older. If somebody was attacking your modem, you wouldn't be able to use any software to discover anything about it as none of the malicious communication would be being transmitted to your computer.

This does remind me of a story I read once:

> I know a woman that believes there is a hacker attacking her computer. Every time there is a problem, or she gets an error message she is convinced it is "the hacker" messing with her. Almost every day she tells me "The hacker made me lose my document" or "The hacker made my email return with a wrong address message" or "The hacker made Explorer freeze today" or "The hacker made Napster lose its connection today" or "The hacker made a floppy unreadable" or "The hacker made the printer jam."

She has even assumed her imaginary enemy has superhuman powers. When I tell her some of the things she says are impossible to do, she says, "He knows how to do it. He is a genius."

She is sure this guy exists, and he devotes enormous resources and several hours a day, seven days a week to the sole purpose of bothering her.

> Is there a program that put ALL authorizations on "Authorize" with ONE STROKE
like F10 and then F11 fot Default - that would be so nice

I have no idea what you mean by "all authorizations on 'Authorize'". What authorizations?

---

### Post by Sidewinder1 on 2009-07-18
Hey 3rdalbum, to this are you referring?
It's sad but also funny in a sadistical way.
[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)
It's long but well worth the read.
Sorry to almost hijack this thread but I couldn't resist...

Side

---

### Post by HotForLinux on 2009-07-18
> **Paqman said:**
> 
Linux comes with a firewall system built in. A good tool for managing it is gufw.
.

I have ufw, but why is gufw package not on Hardy?

P.S. Naaah!... I don't think it's the russian mafia (do you see any around here?) nor Google employees, ....sounds much more like the CIA.

---

### Post by twright on 2009-07-18
If you  believe you are genuinely being hacked then I suggest you simply unplug your computer from the Internet and then do (another) fresh install of Ubuntu. Then if your problems continue you will be certain they are hardware related.

Can you be more specific about what you are experiencing and post screenshots and log files as appropriate. As you can see from previous similar posts without technical information to confirm your situation many will jump to conclusions as many reporting similar issues may simply have been paranoid.

Ubuntu's default install is secure and should not be trivial even for advanced/professional hackers to compromise remotely. It does not have a firewall by default as there are no open/attackable ports by default however if you want to enable one you can using gufw or the commands:
```
sudo ufw default deny
sudo ufw enable
```A more plausible idea is that your router many have been hacked, if you search online there are many ways to check whether this may be the case. Whether you are being actively hacked or people are just playing games with you there are ways to check/find out and there is no need to panic.

@Hot For Linux
gufw is not in Hardy as it did not exist when hardy was released. If you want to install it you will either need to see if it is in backports or wait for the next LTS release/upgrade to Jaunty.

As for the CIA's involvement if they were spying on you they certainly (hypothetically) would not let you know :-)

---

### Post by kain1 on 2009-07-18
> **Paqman said:**
> Hi, i'm a bit confused by this. What do you mean when you say "my modem initialised"? Can you be more specific about what the actual problem is?

However, i'd say it's highly unlikely anyone is attacking you. Despite the threats that some people throw around the internet, you can rest assured that the vast majority of people you offend will have no actual way of attacking you. Unless you're trolling on black hat hacking sites, I guess...



I highly doubt Google employees are involved, you're being paranoid.



Linux comes with a firewall system built in. A good tool for managing it is gufw.



That would suggest that the problem is your hardware, but without a better idea of what is happening it's hard to say.



Go to System > Admin > Log file viewer. From there you can go to View > Find and search for what you're interested in.
Thank Pakman - but
they are Black Hat kind
exploiting a religious site
and a hard sex site at the same time

and all these sites are hyper professionnal
& amazing to see

Thanks I ll check the hardware first now
(vacuum cleaner)

---

### Post by kain1 on 2009-07-18
> **twright said:**
> If you  believe you are genuinely being hacked then I suggest you simply unplug your computer from the Internet and then do (another) fresh install of Ubuntu. Then if your problems continue you will be certain they are hardware related.

Can you be more specific about what you are experiencing and post screenshots and log files as appropriate. As you can see from previous similar posts without technical information to confirm your situation many will jump to conclusions as many reporting similar issues may simply have been paranoid.

Ubuntu's default install is secure and should not be trivial even for advanced/professional hackers to compromise remotely. It does not have a firewall by default as there are no open/attackable ports by default however if you want to enable one you can using gufw or the commands:
```
sudo ufw default deny
sudo ufw enable
```A more plausible idea is that your router many have been hacked, if you search online there are many ways to check whether this may be the case. Whether you are being actively hacked or people are just playing games with you there are ways to check/find out and there is no need to panic.

@Hot For Linux
gufw is not in Hardy as it did not exist when hardy was released. If you want to install it you will either need to see if it is in backports or wait for the next LTS release/upgrade to Jaunty.

As for the CIA's involvement if they were spying on you they certainly (hypothetically) would not let you know :-)
Thaks Richard - yes the hardware OK now
and reinstall yes I did and the problems start
when I reconnect to their site , a blog site

Concerning the modem  ADSL ,  the password for the ISP is wiped
so I have then completely reset & re config

Thanks and I try what you said

---

### Post by kain1 on 2009-07-18
> **HotForLinux said:**
> I have ufw, but why is gufw package not on Hardy?

P.S. I don't think it's the russian mafia (do you see any around here?) nor Google employees, ....sounds more like the CIA.
CIA  -  Hé  Yes that could be
because I have send a nice word
to the White House for felicitation
adding a nice idea for the economy

Make me think on an other occasion
long ago : after sending a letter to
the french first Lady and her AIDS foundation
and oferring an idea

---

### Post by twright on 2009-07-18
> **kain1 said:**
> Thaks Richard
Just to clarify I am not [Richard Stallman]("http://en.wikipedia.org/wiki/Richard_Stallman"), that is just my signature :D

---

### Post by kain1 on 2009-07-18
> **kain1 said:**
> CIA  -  Hé  Yes that could be
because I have send a nice word
to the White House for felicitation
adding a nice idea for the economy

Make me think on an other occasion
long ago : after sending a letter to
the french first Lady and her AIDS foundation
and oferring an idea
I was interupted - perhaps maximum of words and than sending automatically what I wrote
HOW DANGEROUS IS THAT -
anyway  what I wanted to tell
the MONTHS after that letter we were regulary embarred
by helicopters in our french beach house

Can you believe that
Hrelicopters at 2 meter altitude before the kitchen windows
like
"Thou shall not send letters to the Pres"
My wife saying : I'm Naive

---

### Post by kain1 on 2009-07-18
> **3rdalbum said:**
> So you're saying that they are tracking you across a change of operating systems and across your (presumably daily) change of IP addresses? And that they're spending all their time hacking into Youtube just to annoy you?

That's highly implausible. The problems with your modem are most likely hardware problems, and getting worse due to your modem getting older. If somebody was attacking your modem, you wouldn't be able to use any software to discover anything about it as none of the malicious communication would be being transmitted to your computer.

This does remind me of a story I read once:





I have no idea what you mean by "all authorizations on 'Authorize'". What authorizations?
There is in ADMINISTRATOR > AUTHORIZATIONS
AND A LOT OF TIMES
when you go in there is said 
AUTHORIZATION INDEFINATELY
and I want to change that in 
AUTHORIZE or sometimes in NO

BUT IT IS A LOT OF WORK

i understand tha when filling in AUTORIZE
Ubuntu will ask the password which I find a nice secure way
that almost NO PROGRAM LINE or script
can be activated without local  password

aND THANKS FOR THE STORY

But is there some eve,n FOR SALE !!  a program
that does the AUTHORIZE STUFF for us
and another that monitors all the logs for us  ??

---

### Post by kain1 on 2009-07-18
> **Sidewinder1 said:**
> Hey 3rdalbum, to this are you referring?
It's sad but also funny in a sadistical way.
[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)
It's long but well worth the read.
Sorry to almost hijack this thread but I couldn't resist...

Side
I read it
and laughing somewhat
yes the Bios, that might be dust

but yes I feel stupid

Question
CAN *.wmp BE INFECTED  ??

It started after they sent me a VID. and it took remarkably long time
to open under Linux and did one frame per second  ,  super slow  and it was only really viewable under windows
where only one of 5 players showed the content : THAT WAS WITH BSPLAYER.EXE
doing the job but only after a warning that the content was corrupted.

---

### Post by 3rdalbum on 2009-07-18
> **kain1 said:**
> There is in ADMINISTRATOR > AUTHORIZATIONS
AND A LOT OF TIMES
when you go in there is said 
AUTHORIZATION INDEFINATELY
and I want to change that in 
AUTHORIZE or sometimes in NO

BUT IT IS A LOT OF WORK

i understand tha when filling in AUTORIZE
Ubuntu will ask the password which I find a nice secure way
that almost NO PROGRAM LINE or script
can be activated without local  password

aND THANKS FOR THE STORY

But is there some eve,n FOR SALE !!  a program
that does the AUTHORIZE STUFF for us
and another that monitors all the logs for us  ??

To what end?

Most items in the Policykit "Authorizations" settings are not anything to worry about - changing the CPU scaling, for instance. Ubuntu ships with sane, secure defaults. If you want to change them, change them - it's easy, it's all GUI, and you don't have to do them all in case you're worried about hackers turning your Bluetooth on and off.

If the supposed attackers have an active console running on your machine that can authenticate to root, then NO POLICYKIT SETTINGS WILL SAVE YOU.

Your WMV video file was probably corrupted if only one player would deal with it. There is such a thing as a "maliciously crafted file" that, when opened, will compromise the program and cause it to run commands, and this has been done before for Windows Media Player. But, just as Freud said "Sometimes a cigar is just a cigar", 99% of the time a corrupted video file is just a corrupted video file, not the Russian Mafia taking revenge on you for mocking their religion.

I'm sorry, but I don't believe for one moment that some genius hackers are tracking you and cracking your computer and router. Unfortunately the anti-virus vendors in the Windows world spread so much fear of computer attacks that it's quite common for people to reach for the anti-virus software whenever their computer does anything slightly unexpected.

Sidewinder1: Thanks for the link, I hadn't seen that thread before.

---

### Post by ufolx on 2009-07-18
some kind of funny this thread :P

---

### Post by Sidewinder1 on 2009-07-18
Welks 3rd. It's an oldie but a goodie.
:-)

---

### Post by NOTAGEEK on 2009-07-18
> **kain1 said:**
> So when I visit them, -after I offended them once - it's a religious site/blog -  they have initiazed my modem 5 times now
and do other strange things.

They even did this 1 time when I acceded their YOUTUBE page where I was already blocked
The moment I tried to subsribe again it appened
THIS SEEMED ALMOST IMPOSSIBLE TO ME
and mede me think that Google Employees were involved.


So, .  . I cleaned my PC from all text files etc , and even bought 4 Hard Drives
all completely virgin with Ubuntu 9.04 /daily update - NOT automatic ( wow )

Is there a firewall  like BLACKICE for Windows, to better see where it's coming from and how ?

This started on my Windows XP and therefore I changed to Linux.
It seems to me that they know Linux much better than Windows
All symptoms grew worse


Is there a program that put ALL authorizations on "Authorize" with ONE STROKE
like F10 and then F11 fot Default - that would be so nice

Is there software to analyse the Logfiles more automatically

Kain1



1. write this email address on a piece of paper...  [email]info@messages.whitehouse.gov[/email]

2. put this paper under your pillow along with a baby tooth... if you dont have a baby   tooth they are usually available on ebay cleverly disguised as body parts are on the SL there...

3. the tooth fairy will let your stalkers know that you are on to them through a dream...

4. if you have really been behaving well lately you might find a coin or two under your pillow in the morning... this is of course not guaranteed...

5. your computer problems will then be a thing of the past... guaranteed !!!

---

### Post by HotForLinux on 2009-07-18
> **kain1 said:**
> CIA  -  Hé  Yes that could be
because I have send a nice word
to the White House for felicitation
adding a nice idea for the economy

Make me think on an other occasion
long ago : after sending a letter to
the french first Lady and her AIDS foundation
and oferring an idea

Yes! But maybe your message was intercepted by some hackers, the Google employees, by your neighbours or by Abel1


I don't think you are being attacked by the White House because you don't like Obama, Do you?

---

### Post by HotForLinux on 2009-07-18
How do you know for sure that you are not being attacked by extraterrestrial intelligent and magic powers?

---

### Post by lavinog on 2009-07-18
> **kain1 said:**
> 
CAN *.wmp BE INFECTED  ??

There were cases where the drm code in a media file actually installed malicious code.
Your situation could be that they are attacking your modem. Some isp companies will allow you to swap out your modem with a newer (and more secure usually) one. You may want to try that.

---

### Post by HotForLinux on 2009-07-18
```
user@windoze:~$ cowsay -f satanic -p From Russia With Love
 ______________________
< From Russia With Love >
 ----------------------
     \
      \  (__)  
         (\/)  
  /-------\/    
 / | 666 ||    
*  ||----||      
   ~~    ~~  

```

---

### Post by t4thfavor on 2009-07-18
Thats awesome:

```

_______________________________________
/ Usually its Russian dudes attacking   \
| some poor naked redhead on sites like |
\ that!                                 /
 ---------------------------------------
     \
      \  (__)  
         (\/)  
  /-------\/    
 / | 666 ||    
*  ||----||      
   ~~    ~~     

```

---

### Post by lavinog on 2009-07-18
> **Sidewinder1 said:**
> Hey 3rdalbum, to this are you referring?
It's sad but also funny in a sadistical way.
[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)
It's long but well worth the read.
Sorry to almost hijack this thread but I couldn't resist...

Side

I can't believe that I got sucked into that.
I suspect that the cdrom drive was defective. My 4 year old sony dvd-rw drive had to be replaced earlier this year because it would read disks inconsistantly

---

### Post by bodyharvester on 2009-07-18
i lolled at this thread, i really did

---

### Post by bodhi.zazen on 2009-07-18
gotta love the satanic cow.

@kain1 - don't visit the site in question, lol.

Otherwise, get a new router and read :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

If that does not fix your problem, you may need the kind of professional help that is beyond what these forums can provide.

Good luck.

---

