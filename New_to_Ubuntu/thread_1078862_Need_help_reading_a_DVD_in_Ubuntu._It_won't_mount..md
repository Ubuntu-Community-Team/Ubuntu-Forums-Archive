---
title: "Need help reading a DVD in Ubuntu. It won't mount."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Bushcraft Bill on 2009-02-23
my desktop is 100% running under ubuntu but it can not read a dvd that was burnt with vista since I get alot of stuff from people on dvd this makes ubuntu usless to me it keeps coming up with cannot mount volume if their is not a fix soon coming in one of the updates I will have to go back to vista and forget about ubuntu if it can not do this one simple task of reading a dvd ....

---

### Post by taurus on 2009-02-23
It depends how you burnt the darn DVD in vista.

---

### Post by howefield on 2009-02-23
> **Bushcraft Bill said:**
> my desktop is 100% running under ubuntu but it can not read a dvd that was burnt with vista since I get alot of stuff from people on dvd this makes ubuntu usless to me it keeps coming up with cannot mount volume if their is not a fix soon coming in one of the updates I will have to go back to vista and forget about ubuntu if it can not do this one simple task of reading a dvd ....

And your point is ?

Is this a question, threat or simply a state of play ?

---

### Post by albinootje on 2009-02-23
> **Bushcraft Bill said:**
> forget about ubuntu if it can not do this one simple task of reading a dvd ....

Can you post the output of :
```

dmesg | grep -i dvd
lspci

```
Perhaps your dvd-drive or BIOS needs an (firmware) upgrade.

---

### Post by Bushcraft Bill on 2009-02-23
no idea what so ever of what you are saying... were do you do something like that in a word processer or in the bios thing or what....

> **albinootje said:**
> Can you post the output of :
```

dmesg | grep -i dvd
lspci

```
Perhaps your dvd-drive or BIOS needs an (firmware) upgrade.

---

### Post by albinootje on 2009-02-23
> **Bushcraft Bill said:**
> no idea what so ever of what you are saying... were do you do something like that in a word processer or in the bios thing or what....

Run Ubuntu from the "live session" from the Ubuntu installation cdrom, fire up a terminal (-> Applications -> Accessories -> Terminal), and copy and paste those commands.
After that copy and paste the results, and post them here.

---

### Post by Bushcraft Bill on 2009-02-23
it only burns it one way onto the dvd

> **taurus said:**
> It depends how you burnt the darn DVD in vista.

---

### Post by dorado29 on 2009-02-23
this is going to be well received...

---

### Post by Bushcraft Bill on 2009-02-23
why cuz no one has a clue how to fix it seems to be an ongoing problem from what I have been reading in the forum threads here so are they going to fix the problem or just let it slide guess I will go mac and vista is crap to meny viruses that kick the crap out of it....

I guess reality is not welcome here then from what your saying...



> **dorado29 said:**
> this is going to be well received...

---

### Post by Yashiro on 2009-02-23
Can you read DVD's you burn yourself?
Can you read movie DVDs?
Can you read CD's burnt in Vista?

---

### Post by Bushcraft Bill on 2009-02-23
I can burn to dvd on the ubuntu puter - yes!
I can see movies burnt from my Visa puter - yes
I can read cd's burnt with vista - yes!

I can not read any files/documents on DVD burnt with vista - no!

> **Yashiro said:**
> Can you read DVD's you burn yourself?
Can you read movie DVDs?
Can you read CD's burnt in Vista?

---

### Post by Bushcraft Bill on 2009-02-23
man this server keeps crashing 8th time I have had to retry and get into the site...

---

### Post by Ng Oon-Ee on 2009-02-23
Have you followed the instructions given earlier by albinootje?

Nobody here magically knows all about your system and what the problem is. If a doctor asks you to describe your illness and you say "I'm sick!" that doesn't help very much, does it?

---

### Post by rocketflame on 2009-02-23
well vista does sometimes burn in some stupid vista only format, dont know too much about it though.

---

### Post by Yashiro on 2009-02-23
Ok.

Open Applications, Accessories, Terminal.
Type > sudo gedit /etc/fstab
Look for the line similar to
> /dev/scd0 /media/cdrom0 **udf,iso9660** user,noauto,exec,utf8 0 0

and change it to
> /dev/scd0 /media/cdrom0 **auto** user,noauto,exec,utf8 0 0

ie remove the text udf,iso9660 and replace it with auto. Do not alter anything else.

Save the file and reboot. 

It's not a failing of Vista, it's possibly a failing of Linux to read udf format discs.

---

### Post by bakedbeans4life on 2009-02-23
> **rocketflame said:**
> well vista does sometimes burn in some stupid vista only format, dont know too much about it though.

Could this have anything to do with the "Live File System" facility that Vista has?

An excerpt from [http://blogs.techrepublic.com.com/window-on-windows/?p=536](http://blogs.techrepublic.com.com/window-on-windows/?p=536)

"The default version of the Live File System is only readable by Windows XP and Vista systems, and the Live File System works differently with the various types of optical discs."

Just a thought.

---

### Post by huzzam on 2009-02-23
> **Bushcraft Bill said:**
> I guess reality is not welcome here then from what your saying...

I'd say anger and threats are what's not well-received. Are you asking for help, or do you just want to yell at someone?

Keep in mind that the people on this forum are all volunteers, helping in their free time out of generosity.

---

### Post by protodog on 2009-02-23
Hey Bushcraft Bill,

Can you post the output to what albinootje and Yashiro are asking in their posts? We're trying to help you here, but we need more information about what's going on.

-protodog

---

