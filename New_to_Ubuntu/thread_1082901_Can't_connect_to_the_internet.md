---
title: "Can't connect to the internet"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Quagga7 on 2009-02-28
I hava problem i had to completely reinstall ubuntu
an it finally gave a conncetion! but i try to connect to the internet but it gave mi this message


"Your operating system is not supported by Comcast's Installation Wizard......"

---

### Post by arm-c on 2009-02-28
Don't try to use the instal CD they gave you.

I don't use comcast.  Call them and get a tech support GURU on phone and they should be able to help you.  Might get the "we don't support linux" line, but press forward, ask to speak with a representative, etc... Still, I wouldn't think you would even need to call, as you should pull an IP via DHCP automatically.

What are you connecting through (cable modem directly or a secondary router (ie wireless).  Still shouldn't make a difference.

What is it you are DOING EXACTLY (loading CD, installing X, etc...) when you get that error.

NOTE:  While linux can run some windows programs with Wine, it is not for all applications and I stay away from it when I can.  In almost all cases, I have found a native linux version of some software that does what I want to do (just might not be same program as windows).

---

### Post by scrooge_74 on 2009-02-28
You need to post exactly what method you use to conect to internet. What ever CDs or any other stuff you used in Windows wont work with linux. As long as your network cards (wifi or wired) are properly recognize and have drivers, your issue is with your provider.

Be it that you need to manually put IPs or DHCP information, etc. But forget about any CDs they gave you that wont work now. Was the CD to get some USB modem working?  Tell more so people can help

---

### Post by Quagga7 on 2009-02-28
NO its not the CD the OS is ubuntu linux 8.10
my internet works fine on my laptop which runs on windows xp
but it doesnt run on my desktop it runs on linux. i connect my eithernet cable to my desktop, it says the auto eth0 is connected i open my browser firefox and it pops out the comcast message
"Your operating system is not supported by comcast's installation wizard..." so i dont know what to do is there a way u guys can help me?!
also i have the wine package on my desktop but i dont know how to install it with out the internet. 

X[

---

### Post by arm-c on 2009-02-28
Hmmm,

What is the Firefox URL when you get the message?

---

### Post by albinootje on 2009-02-28
> **Quagga7 said:**
> i connect my eithernet cable to my desktop, it says the auto eth0 is connected i open my browser firefox and it pops out the comcast message


Can you please post the output of the following commands in a terminal:
```

ifconfig -a
route -n
cat /etc/resolv.conf
ping -c3 194.109.21.51

```

---

### Post by arm-c on 2009-02-28
Read the link at the attached file:
[http://techliberation.com/2008/04/15/dance-dance-revolution/]("http://techliberation.com/2008/04/15/dance-dance-revolution/")

This is apparently a COMCAST thing where they are selectively blocking.  I'd call COMCAST and complain about that and have them remove the block.

If the link there is factual (and given your information, sounds so) I'd be livid and ... well, I shall keep my words to myself.  To me, it sounds illegal and wrong...

You also might check out this thread:
[http://www.usenet-forums.com/linux-networking/62905-initial-comcast-setup-linux-possible-without-ms-windows.html](http://www.usenet-forums.com/linux-networking/62905-initial-comcast-setup-linux-possible-without-ms-windows.html)

The thread above recommends that you contact COMCAST and have them tell you all the settings that need to be set and what they need to be set to.  Then we can plug them in... I can't see where there would be any problems with linux because all of the protocols are standard and open for the internet / networking.  

Hope this helps, but it isn't Ubuntu or Linux... (most likely).

---

### Post by Quagga7 on 2009-02-28
here 
[http://www.sendspace.com/file/paxxrk](http://www.sendspace.com/file/paxxrk)


o yeah i want to know how to solve this problem without calling comcast

---

### Post by arm-c on 2009-02-28
I'm out.  I have no suggestions and recommend that you REALLY do call COMCAST to find out what the settings should be.  Then, all you have to do is figure out where to adjust those settings and you should be up and running.

"give a man a fish, feed him for a day... teach him to fish, feed him for a lifetime."

---

### Post by albinootje on 2009-02-28
> **Quagga7 said:**
> here 
[http://www.sendspace.com/file/paxxrk](http://www.sendspace.com/file/paxxrk)

Congratulations, you have internet connection.
I assume that the DNS-server are OK, and working well.

And I'll attach your screenshot to make it easier for others to watch it too.

---

### Post by Quagga7 on 2009-02-28
...

---

### Post by Quagga7 on 2009-02-28
[http://www.sendspace.com/file/etiz8r](http://www.sendspace.com/file/etiz8r)

see!

---

### Post by arm-c on 2009-02-28
Quagga,

You have connection, but because COMCAST is not using a standard configuration setting -- you need to get the information from COMCAST in order to configure your stuff to point to the right DNS.  Read the post I sent you links to (the second one)... especially about 1/2 way down.

Look, your only option now is to CALL COMCAST to get the correct information so you can get past their server.  YOU DO HAVE CONNECTIVITY... it just isn't getting past their servers.

It isn't ubuntu either... I mean they are failing to address the linux OS in software...  It is sad that they haven't learned to be net-neutral and use a platform independent solution.

---

### Post by DGortze380 on 2009-02-28
Preface - I haven't read the whole thread

Comcast does this lovely trick where they forward all requests to their internal DNS until you 'register' from a windows computer with their CD.

In the past I've been able to bypass this by:
clearing all caches
attaching a router to the cable modem
releasing and renewing DHCP for the modem. 

On occasion I've had to manually changed my DNS to opendns, then I'm able to pull down the correct Comcast DNS via DHCP.

---

### Post by arm-c on 2009-02-28
> **DGortze380 said:**
> Preface - I haven't read the whole thread

Comcast does this lovely trick where they forward all requests to their internal DNS until you 'register' from a windows computer with their CD.

In the past I've been able to bypass this by:
clearing all caches
attaching a router to the cable modem
releasing and renewing DHCP for the modem. 

On occasion I've had to manually changed my DNS to opendns, then I'm able to pull down the correct Comcast DNS via DHCP.

Thanks DGortze... perhaps this will help him out.  My last post in this thread.

---

### Post by Ms_Angel_D on 2009-02-28
Please let us know if you get this issue resolved. I am a comcast customer myself and would like to know what happens.

---

### Post by Quagga7 on 2009-03-01
well i have another question how do u install wine without using the internet i hav it saved on my desktop but i dont know how to install it

---

### Post by lemmof on 2009-07-31
> **DGortze380 said:**
> Preface - I haven't read the whole thread

Comcast does this lovely trick where they forward all requests to their internal DNS until you 'register' from a windows computer with their CD.

In the past I've been able to bypass this by:
clearing all caches
attaching a router to the cable modem
releasing and renewing DHCP for the modem. 

On occasion I've had to manually changed my DNS to opendns, then I'm able to pull down the correct Comcast DNS via DHCP.

This sounds like great advice but I don't know how to: clear all caches (what caches??) or release and renew DHCP for the modem.  Is it possible to be more specific?

Every time I call comcast they tell me they can't help me.  I can't even get a consensus on whether my connection is set up on their end or not.

Edit: After a few more phone calls, I managed to get through to somebody who was willing to help me.

---

