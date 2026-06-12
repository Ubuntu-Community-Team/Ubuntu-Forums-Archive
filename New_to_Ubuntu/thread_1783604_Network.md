---
title: "Network?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-15
I downloaded Ubuntu three days ago and in the first half hour I was able to connect to the internet and send email.  I've downloaded all the recommended software and now nothing works because I don't have a network.  Going by your definition of a network I can't believe you want me to install a second computer so what's going on?  How do I get back to the beginning where Ubuntu worked?

Please don't give me a string of code to enter because it won't enter because I don't have a network.  If I need to reinstall Ubuntu how do I do that without a string of code?  (See previous sentence.)  I've been very excited about  using Ubuntu until it stopped doing anything other than making noises when it started but the Help file doesn't have anything remotely close to answering my question.

Why do I need a network?

Randy St. John
[EMAIL="randini321@yahoo.com"]randini321@yahoo.com[/EMAIL]

---

### Post by critin on 2011-06-16
You don't need a network.  Did you edit your internet connecton on the top panel?  Mine has an 'enable network' option to check but that's because I do have a network.  If I uncheck it my internet is disabled.  

Before I set the network up though, it was only the internet connection that ubuntu sets up automatically.  If there is an 'enable network' check box there and you haven't checked it because you don't have a network, check it anyway.  Unless something else has changed your internet should come on.

---

### Post by rs321 on 2011-06-16
critin,

Thanks for the reply but unfortunately I don't get the option to enable the network.  What I get is an error box saying I don't have a network.  I could get of the net yesterday but any sort of option I get now is a place for filling in a bunch of technical jargon that I wouldn't know if I knew what it was.

-Randy

---

### Post by AlbertoEdhek on 2011-06-16
> **rs321 said:**
> critin,

Thanks for the reply but unfortunately I don't get the option to enable the network.  What I get is an error box saying **I don't have a network**.  I could get of the net yesterday but any sort of option I get now is a place for filling in a bunch of technical jargon that I wouldn't know if I knew what it was.

-Randy
hello,
maybe there are some things wrong with your PC. Have you checked your interface (e.g. wireless adapter, LAN Card)?

---

### Post by critin on 2011-06-16
<<<it stopped doing anything other than making noises when it started.>>

Is ubuntu growling at you?  This sounds like more than a missing internet.  It shouldn't make noises.  I would probably check my disk for errors and then reinstall the os.  It really is worth it.   ;)

---

### Post by rs321 on 2011-06-16
No, it doesn't growl; it makes a few notes of some tune.  I don't have Ubuntu on a CD, if that's what you mean by disk.  The hard drive is as clean and stable as it can be made.

I just looked at Ubuntu again to see if I might have missed a switch or option and Firefox (I've been using it for several years) has decided not to open anymore, not even to tell me I can't do something with it because I don't have a network.

I have Ubuntu on a flash drive so I'll try reinstalling it over itself but I'd rather start from scratch so it won't become more confused than it is.

I have a CD writer and a DVD writer but they aren't working at present and there's nothing I haven't tried that will get them going again so I can't burn any codes onto a disk.

My next step is to put the hard drive into the microwave and try erasing it that way.  Just kidding, but I would really like to get the program running with whatever it takes but the Help files aren't any help.

It would probably help if I knew what the initials\acronyms meant when Ubuntu asks me about them but they're not listed in the Help files either.

Thanks for taking an interest.

-Randy

---

### Post by dFlyer on 2011-06-16
What software did you install?

---

### Post by rs321 on 2011-06-16
Howdy,

11.04 through a flash drive then downloaded all (160?) recommended downloads from  Ubuntu.

-Randy

---

### Post by critin on 2011-06-17
Well Randy, I am a newbie though I've played with ubuntu for a few years.  I usually play with it until I break something and then I reinstall again.  I learn that way.  
I've never had a problem with my wired internet, though I've seen many posts for wireless help.  If you're using wired and the issue is with a network, I'd bet you clicked something about network somewhere.  It doesn't wake up by itself in my experience, and I do use a network.  It takes some clicking to get it going.

Your install is new so I'd reinstall and not touch the network or internet settings at all next time.  You said it worked for awhile so you know it's capable.  It automatically finds the peripherals as it installs, you shouldn't have to edit them.

Good luck and let me know how you did.
critin

---

### Post by crispy_420 on 2011-06-17
Has nobody commented on the miswording initially used on this post?

It is not "enable network" it is "enable networking". There is a difference in the terms. If you uncheck it you essentially disable the ability to communicate with other systems/computers and that includes the internet. So unchecking this feature is the same as just yanking out your network cable. Make sure this stays checked. 

If you right click and select "edit connections". Under wired you should see "Auto eth0", select that and pick edit. Make sure the IPv4 tab has the method of "Automatic (DHCP)" selected. If you change it use apply at the bottom. 

Did get you anywhere? If you right click where "enable networking" select connection information. What is your IP? Subnet mask? Primary/Secondary DNS? These are the basics that get you online.

---

### Post by jtarin on 2011-06-18
> **rs321 said:**
>  Going by your definition of a network I can't believe you want me to install a second computer so what's going on?I don't remember sending you a definition......but then...I am getting old.:p  

> **rs321 said:**
> Please don't give me a string of code to enter because it won't enter because I don't have a network.Normally stings of code are entered in a terminal, a network (internet connection)is only needed to do do the things an internet connection normally allows you to do.> **rs321 said:**
>    If I need to reinstall Ubuntu how do I do that without a string of code?Use an install CD/DVD or USB flash.> **rs321 said:**
>   I've been very excited about  using Ubuntu until it stopped doing anything other than making noises when it started but the Help file doesn't have anything remotely close to answering my question.I would still be very excited if my Ubuntu install was making noises.....how unique is that?:p

> **rs321 said:**
> Why do I need a network?So you can come here and learn many wondrous things.:p

> **rs321 said:**
> Randy St. John
[EMAIL="randini321@yahoo.com"]randini321@yahoo.com[/EMAIL]It's not a good practice to post your email in the open....ya know! spambots and all that.

---

### Post by critin on 2011-06-18
> **crispy_420 said:**
> Has nobody commented on the miswording initially used on this post?

It is not "enable network" it is "enable networking". There is a  difference in the terms. If you uncheck it you essentially disable the  ability to communicate with other systems/computers and that includes  the internet. So unchecking this feature is the same as just yanking out  your network cable. Make sure this stays checked. 
.

So ubuntu's definition of networking is different than the dictionary  and the way I define it?   That is  confusing.   I know I need the  internet to network, but I don't need a network to use the internet.   Since the OP did have internet for a short while, I thought he may have clicked something for 'network' since that's when the  problem came in.  I thought he may have become confused with the terms.   

Apparently I'm the confused one.  Do references to 'networking' truly  mean the 'internet'?  Maybe that's why I had problems before I repeated  the process a few times and read a ton of forum posts.  Guess I need to read some more.

In post #2  I mentioned he should check and make sure he had not   unchecked 'enable network (ing)' so the internet may become enabled  again.  He didn't need or want a network and newbies such as we are  might naturally uncheck it.  My internet is always enabled upon  installing, but I had to enable any lan network myself.  It was never  checked automatically.  Maybe a difference in the versions or something?

I'm sorry if I misspoke but he was clear about how he was defining  'networking' and I answered him according to my own newbie experience  and what works for me.  Reinstall and don't edit what works.  :wink:

<<What is networking? 
Networking in the field of computing is the practice of linking computer  devices together to support digital communication among them.  Printers, etc.

What is a Network?
A network consists of two or more computers that are linked in order to share resources>>>

And of course there's Social Networking that doesn't need a lan network--but it does require an internet connection.  :smile:

Thanks for the help.

critin

---

### Post by 3rdalbum on 2011-06-18
Try shutting down the computer completely, removing the battery and putting it back in (if it's a laptop) and then starting up again.

---

