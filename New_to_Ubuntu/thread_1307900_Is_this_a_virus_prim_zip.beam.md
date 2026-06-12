---
title: "Is this a virus: prim_zip.beam"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by metalaxesucks on 2009-10-31
I have Ubuntu 9.10
I scanned with KlamAV & it says prim_zip.beam is a virus

Location is here:
/usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam

Thanks

---

### Post by yeats on 2009-10-31
I seriously doubt it.  What is the output of

```
file /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam
```?

---

### Post by ranch hand on 2009-10-31
I take it that this is the add on for blender that you are referring to.

---

### Post by Liolikas on 2009-10-31
Reinstall erlang-base if still same then fake report.

---

### Post by NoaHall on 2009-10-31
AV's on Linux OS's don't really work, as the "viruses" they report are either vital files which they can't handle, or just files which may damage Windows systems, not your own Linux OS.

---

### Post by metalaxesucks on 2009-10-31
> **chrissharp123 said:**
> I seriously doubt it.  What is the output of

```
file /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam
```?


When I ran your commend in the terminal it gave me this:
/usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam: Erlang BEAM file

---

### Post by peculiar penguin on 2009-10-31
[http://www.virustotal.com/analisis/7a3f470df29912061f7b72302ff42e33605617fbffe5ab42fa458235a7e491cd-1257007294](http://www.virustotal.com/analisis/7a3f470df29912061f7b72302ff42e33605617fbffe5ab42fa458235a7e491cd-1257007294)

[http://en.wikipedia.org/wiki/False_positive#Malware](http://en.wikipedia.org/wiki/False_positive#Malware)

---

### Post by metalaxesucks on 2009-10-31
> **peculiar penguin said:**
> [http://www.virustotal.com/analisis/7a3f470df29912061f7b72302ff42e33605617fbffe5ab42fa458235a7e491cd-1257007294](http://www.virustotal.com/analisis/7a3f470df29912061f7b72302ff42e33605617fbffe5ab42fa458235a7e491cd-1257007294)

[http://en.wikipedia.org/wiki/False_positive#Malware](http://en.wikipedia.org/wiki/False_positive#Malware)

I checked to see if I could find the same file on my USB bootup stick, & I did. This fact, plus the scan results in your link convinces me than this is a false positive.
Thanks everybody for your help :D

---

### Post by Independent Lion on 2009-10-31
Hi friends.My results

[IMG]http://img257.imageshack.us/img257/8598/screenshot1no.png[/IMG]

---

### Post by Joe Ker1086 on 2009-10-31
So is there any anti-virus software that runs well on Linux?

---

### Post by ikacer on 2009-10-31
> **Joe Ker1086 said:**
> So is there any anti-virus software that runs well on Linux?

linux generally doesn't need antivirus. you can read more about it here:
[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")


Cheers.

---

### Post by ranch hand on 2009-10-31
All this AV scanning is primarily used to protect poor MS users from things you may pass on to them.

I think that they can take care of their own security, if not, I think and infection or two will cure their problem.

I believe that this came up positive because it is executable, does not run on its own and modifies another executable.

---

### Post by Independent Lion on 2009-10-31
Quarantine process negative.What should ?
Edit:Excuse me

---

### Post by NoaHall on 2009-10-31
> **Independent Lion said:**
> Quarantine process negative.What should ?

Leave it alone, it's meant to be there, and it's not harmful.

---

### Post by liquidbee on 2009-10-31
> **Joe Ker1086 said:**
> So is there any anti-virus software that runs well on Linux?

Try [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") - one of my all time favorites.

---

### Post by Independent Lion on 2009-10-31
> **NoaHall said:**
> Leave it alone, it's meant to be there, and it's not harmful.
I have nothing to complain about.Keeping out of trouble.Been up to no good
it has to be like this.Thank you, that's very nice of you.

---

### Post by Joe Ker1086 on 2009-11-06
> **liquidbee said:**
> Try [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") - one of my all time favorites.

Ill give it a try. I always run AVG and SPYBOT S&D. Can anyone tell me exactly why viruses don't occur on linux as much? Doesn't make a ton of sense to me considering it is all open source and it seems like it would be easier to write viruses on.

---

