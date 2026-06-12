---
title: "Pidgin wont stay connected now"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by misswham on 2009-06-25
Can anyone tell me why pidgin wont stay connected.  I have already updated to the new version and it worked perfect but after one day it logs on and completely off.  I went to bed last night and when I woke up it worked fine for about 20 minutes and now it has started again.  Wont stay connected.  

Please can anyone help me.

---

### Post by misswham on 2009-06-25
i have searched the forum for answers and i will try to change the IP addresses but I cant even get it to stay on to do that.  I am lost. 

Can someone please help me?

---

### Post by dazzlindonna on 2009-06-25
Any chance you're using Yahoo in pidgin? If so, go to the account and "Modify". On the Advanced tab, "Pager server" field, enter one of the following:

cs102.msg.mud.yahoo.com or cs101.msg.mud.yahoo.com

---

### Post by misswham on 2009-06-25
that is actually what i am trying to do but i cant get it to stay on to do that.  as soon as i log on 2 secs it cuts off.

---

### Post by seamonkey09 on 2009-06-25
I'm actually having a problem with Yahoo not connecting, but when I put in the code dazzlindonna provided, it's still not working. 

Any ideas?

---

### Post by nnamdi on 2009-06-25
hey you could try these settings out
```

cn.scs.msg.yahoo.com

```

---

### Post by AgentZ86 on 2009-06-25
Thanks

---

### Post by misswham on 2009-06-25
just got home and the pidgin still wont stay on.  my computer has been off for 8 hrs.  i double clicked the icon and it popped in and right off.  please please please.  i cant function without instant messenger.

---

### Post by misswham on 2009-06-26
i just ran the latest updates and i checked all of them out and none of them said pidgin but after they were over and i restarted, it works.  i dont know why but it did wondering?

---

### Post by misswham on 2009-06-26
cutting off again!  

H E L P!

I am at wits end.  I thought the update did it.  I dont think its the ip address.  it is immediately connecting but immediately turning off.  Does anyone think that I should uninstall it and reinstall it?  If so how?

---

### Post by balachandarlinks on 2009-06-26
Hai,
    You can use prism.Its good.I m facing the same problems ad now changed myself to prism.We can customize prism for any app.It can surely subsitute pidgin.
                  cheers,,,,,,

---

### Post by misswham on 2009-06-26
where do i find it?  i went to synaptic manager and typed it in search and nothing came up

---

### Post by mc4100 on 2009-06-26
> **misswham said:**
> where do i find it?  i went to synaptic manager and typed it in search and nothing came up

Assuming they mean the mozilla labs project, prism is a way to take a firefox web application, like the many many many online instant messaging web pages and run them as stand-alone apps.
[http://www.realgeek.com/gchat-msn-yahoo-messenger-prism/](http://www.realgeek.com/gchat-msn-yahoo-messenger-prism/)

---

### Post by ~sHyLoCk~ on 2009-06-26
Adding the server address to /etc/hosts doesn't help? I tried that once and it worked for me!

---

### Post by nandemonai on 2009-06-26
Ok lets get to the bottom of this. From my understanding pidgin is actually crashing for you yes?

Couple things for you to try..

First confirm the version you're using:

From terminal (Applications -> Accessories -> Terminal) please paste the output of these commands:

```
pidgin -v
```

```
apt-cache policy pidgin
```

Secondly, what happens if you try and run pidgin from the terminal without actually logging in? (Paste any errors)

```
pidgin -n
```

Normally? Again, please paste any errors.

```
pidgin
```

And finally:

```
pidgin -d
```

You might want to [pastebin]("http://ubuntu.pastebin.com/") the last one.

---

### Post by misswham on 2009-06-26
here is the outcome of the first command

-desktop:~$ pidgin -v
Pidgin 2.5.7 (libpurple 2.5.7)

---

### Post by misswham on 2009-06-26
2nd command

-desktop:~$ apt-cache policy pidgin
pidgin:
  Installed: 1:2.5.7-1ubuntu1~pidgin3.8.04.1
  Candidate: 1:2.5.7-1ubuntu1~pidgin3.8.04.1
  Version table:
 *** 1:2.5.7-1ubuntu1~pidgin3.8.04.1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
        100 /var/lib/dpkg/status
     1:2.4.1-1ubuntu2.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
     1:2.4.1-1ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

---

### Post by misswham on 2009-06-26
the third.  it came on but the icon in the toolbar says offline

---

### Post by philcamlin on 2009-06-26
maybe its your isp

---

### Post by misswham on 2009-06-26
the forth it logged on and crashed immediately

-desktop:~$ pidgin
Segmentation fault

---

### Post by philcamlin on 2009-06-26
hmm have you tried empathy or amsn or ebuddy.com

and see if it works :popcorn:

---

### Post by misswham on 2009-06-26
this one was just my blocked list

---

### Post by philcamlin on 2009-06-26
try a web messenger then write back 

see if it works

---

### Post by misswham on 2009-06-26
what do u mean try a web messenger?

---

### Post by misswham on 2009-06-26
It stays on the screen when it says offline but as soon as i try to connect, my friends list comes up then it crashes.

could it be the ip address?

---

### Post by philcamlin on 2009-06-26
[www.ebuddy.com](www.ebuddy.com) 

its an online messenger for wahoo and msn 

try and see if it stays connected on there :popcorn:

---

### Post by raymondh on 2009-06-26
Misswham ..

I would have shutdowns whenever I had an XMPP (google chat) protocol enabled.... 

My solution was to go to disable google chat > go to tools > plugins > enable XMPP > restart > enable google chat 

As for yahoo IM, I did go through the IP changes, using mud and even a china (cn) server.  After upgrading to 2.5.7, I went back to the scs.msg.... (see screenshot) as the workaround servers no longer worked.

So far, no crashes yet. 

Hope this can help.

---

### Post by philcamlin on 2009-06-26
that should do the trick :popcorn:

---

### Post by misswham on 2009-06-26
i just found out that my main yahoo id is the culprit.  when i logged on through the terminal and it was offline, i changed the ip address of the main default yahoo id i have been using since 2001 and when i tried to connect, the main one didnt but all the other id's i use did.  does this make sense to anyone and i couldnt read the prior attachment it was too small.

---

### Post by misswham on 2009-06-26
also when i went to web messenger and meebo the id stayed connected and it worked fine it just didnt work on pidgin.

---

### Post by philcamlin on 2009-06-26
good to hear you fixed it :popcorn:

---

### Post by misswham on 2009-06-26
how is it fixed?  why would my main id that i have used in pidgin for 2 yrs and also that has worked when i upgraded to the new now doesnt work?  my default id is the one that i use.

---

### Post by misswham on 2009-06-27
Finally got it to work for now.  Went to terminal and put in

pidgin -n

It came up but offline.  Went and changed the ip address to

scsa.msg.yahoo.com

and then i reconnected and it worked.  Now it was strange because I have 3 other yahoo id's that have the old ip address and they are connected but i changed the default one to the scsa.msg.yahoo.com and it hasnt crashed.  i am not gonna get my hopes up yet.  We will see.

---

### Post by k3lt01 on 2009-06-27
> **misswham said:**
> i couldnt read the prior attachment it was too small.Did you click on it? if you did it should open up a bigger screen shot that, on my laptop at least is quite readable.

---

### Post by raymondh on 2009-06-27
> **misswham said:**
> Finally got it to work for now.  Went to terminal and put in

pidgin -n

It came up but offline.  Went and changed the ip address to

scsa.msg.yahoo.com

and then i reconnected and it worked.  Now it was strange because I have 3 other yahoo id's that have the old ip address and they are connected but i changed the default one to the scsa.msg.yahoo.com and it hasnt crashed.  i am not gonna get my hopes up yet.  We will see.

Congratulations.

---

### Post by misswham on 2009-06-28
worked fine until just now.  it shut off and now wont stay connected.  whats going on?

---

### Post by balachandarlinks on 2009-06-30
hi jus refresh your synaptic manager and search for "gtalk" or "googlegroups" like that.You ll find prism.For yahoo chat you can try Gyache.Find its deb package on the net.
       You can try Kopete too.It doesnt produce any  errors.

---

### Post by mjh56 on 2009-09-30
> **misswham said:**
> worked fine until just now.  it shut off and now wont stay connected.  whats going on?

I am experiencing same problem, it started when I attempted to authorise a buddy, I have several accounts active and its only when I enable this account that it shuts down, I have tried completely removing pidgin and associated packages pidgin data and libpurple then re-installing but no good. And I did re-boot

Also it does seem to remember my account which means something not being removed, does it store data anywhere about the accounts, if I clear this maybe it will remove whatever wrong

anybody?

---

### Post by mjh56 on 2009-09-30
OK I have got one solution, Pidgin stores the various account info in hidden file .purple in home folder (CNTL-H) to see it, in there is XML file aqccounts.xml, i deleted this. started up pidgin and all accounts lost so  entered them again and everything fine now

---

