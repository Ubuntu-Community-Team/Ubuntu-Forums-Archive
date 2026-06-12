---
title: "Wireshark group and user question"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-22
I see a lot of posts about capture permissions and people saying "type this" and someone saying "hey, worked great!" I guess I'd like to ask a question before I just "type this" so what I think I'm seeing jives with what is really happening.

From the Wireshark wiki: [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)

**Limiting capture permission to only one group**

 1. Create user "wireshark" in group "wireshark". 
2. "chgrp wireshark /usr/bin/dumpcap" 
3. chmod 754 /usr/bin/dumpcap 
4. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap" 
5. Ensure Wireshak works only from root and from a user in the "wireshark" group

Okay so:


[LIST=1]
[*]There is no group created called Wireshark after the install. so this should really read "create group wireshark and then create user Wireshark and make them a member of the group.
[*]fine
[*]fine
[*]fine
[*]Since we don't want to run it as root why run it as root? To see if it only works as a user in the group then I would need to login as that user to run Wireshark right? If the user "wireshark" is a normal user then why not just add myself to the group "wireshark" instead of creating a new user and logging in as that user?
[/LIST]
Thanks for your help.

---

### Post by Rubi1200 on 2010-08-22
Once Wireshark is installed, the correct way to run it without invoking root privileges (which is extremely dangerous) can be done like this from the terminal:

```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

Run each command separately and then run Wireshark.

Courtesy of forum member cdenley.

Hope this helps.

---

### Post by Rumpletumbler on 2010-08-22
Thank you for your help.

I was trying to avoid doing this as per my op.

Any ideas on the questions I asked there?

---

### Post by Rubi1200 on 2010-08-22
> **Rumpletumbler said:**
> Thank you for your help.

I was trying to avoid doing this as per my op.

Any ideas on the questions I asked there?
Ok, I think there may be some misunderstanding here.

If you want to run Wireshark and capture packets, but **not** as root, then you need to use the commands I posted.
 
I have discussed this with both cdenley and bodhi.zazen, both highly experienced members (bodhi wrote the security stickies for the forum), and they advised setting up Wireshark this way.

---

### Post by Rubi1200 on 2010-08-22
Perhaps this is more what you were looking for?

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

Although, I think it boils down to almost the same thing.

Hope this helps.

---

### Post by Rumpletumbler on 2010-08-22
> **Rubi1200 said:**
> Perhaps this is more what you were looking for?

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

Although, I think it boils down to almost the same thing.

Hope this helps.

I was trying to understand why the directions were different and what the differences were and definitely don't want to run the program as root. 

If I just type:

> sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

and it works then that satisfies the working of the program but not necessarily my understanding of why it's done that way and what the differences are between that and the recommendations from Wireshark. 

I do appreciate the help. Thanks.

---

### Post by Rumpletumbler on 2010-08-23
So as I understand it in the first example you're setting up a group and user "wireshark" and giving them permissions to the dumpcap executable. 

In setting it up this way would you have to login as the wireshark user? 

In the 2'nd example you're doing the same thing only with the admin group of which I am a member already and that makes more sense to me as I could run it without logging in as a different user etc. 

I don't really see the need for the additional group and or user.

The only reason I would see using the admin group is if you were going to add others to the admin group who needed to be able to use Wireshark. 

Is that right?

---

### Post by Rubi1200 on 2010-08-23
> **Rumpletumbler said:**
> So as I understand it in the first example you're setting up a group and user "wireshark" and giving them permissions to the dumpcap executable. 

In setting it up this way would you have to login as the wireshark user? 

In the 2'nd example you're doing the same thing only with the admin group of which I am a member already and that makes more sense to me as I could run it without logging in as a different user etc. 

I don't really see the need for the additional group and or user.

The only reason I would see using the admin group is if you were going to add others to the admin group who needed to be able to use Wireshark. 

Is that right?

> In setting it up this way would you have to login as the wireshark user? 
No; as normal user and then run Wireshark from the menu as a normal program.
> Is that right?
Possibly, not sure about this.

Sorry, I am not able to give you a more definitive answer.

---

### Post by Rumpletumbler on 2010-08-23
> **Rubi1200 said:**
> No; as normal user and then run Wireshark from the menu as a normal program.

Any idea how to test this? 

> 5. Ensure Wireshak works only from root and from a user in the "wireshark" group If I set it up this way and then run as myself then of course I'm not testing anything. How would one go about determining that it works only from a user in the Wireshark group? Again, anyone know why this would be more secure than just giving myself permissions to it? I don't get it. :)

---

### Post by Rumpletumbler on 2010-08-31
bump

---

### Post by bodhi.zazen on 2010-08-31
> **Rumpletumbler said:**
> bump

How you choose to manage your users and groups is up to you.

If you want to create a specific group for wireshark you can do so, but you do not need to.

With a single user system it likely makes little to no difference , so long as you are not running wireshark as root.

In terms of your questions re: users and groups, read up on Linux groups.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

From your questions you may not understand what linux groups are or how to set / change your default group.

If you have a more specific question, ask.

---

### Post by Rumpletumbler on 2010-08-31
Thanks for the link. 

I found this [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/) and that explains it better than anything I've seen thus far.

Though still not entirely unconfused it makes a lot more sense.

I'm going to try it this way.

---

### Post by bodhi.zazen on 2010-08-31
> **Rumpletumbler said:**
> Thanks for the link. 

I found this [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/) and that explains it better than anything I've seen thus far.

Though still not entirely unconfused it makes a lot more sense.

I'm going to try it this way.

Are you wanting to know why not run wireshark as root ?

Wireshark is a network aware application and if a cracker is able to crack the wireshark code they would then have root access on your box as wireshark is running as root.

Same as if you are running firefox as root.

---

### Post by Rumpletumbler on 2010-08-31
> **bodhi.zazen said:**
> Are you wanting to know why not run wireshark as root?

No, I understand that. I wanted to be able to understand the pros and cons of doing it the various ways everyone had suggested before I chose one.

It also helps me to start to understand how Linux works if I look at doing something from various angles though it's really overwhelming when nothing quite clicks.

---

### Post by bodhi.zazen on 2010-08-31
> **Rumpletumbler said:**
> No, I understand that. I wanted to be able to understand the pros and cons of doing it the various ways everyone had suggested before I chose one.

It also helps me to start to understand how Linux works if I look at doing something from various angles though it's really overwhelming when nothing quite clicks.

There are almost always 2 or more ways of solving any particular issue such as the one you raise in this thread.

The best option is often a matter of opinion.

Other then that, keep reading.

---

### Post by alphacrucis2 on 2010-08-31
> **bodhi.zazen said:**
> Are you wanting to know why not run wireshark as root ?

Wireshark is a network aware application and if a cracker is able to crack the wireshark code they would then have root access on your box as wireshark is running as root.

Same as if you are running firefox as root.

Are you meaning potential vulnerabilities in Wireshark's code? Surely the same risk exists with the linux kernel which you can't do anything about other than rely on such vulnerabilities being patched in a timely manner if they are discovered. I also think there is a big difference between wireshark and firefox which could be running scripts from arbitrary websites so I don't think that is a valid comparison.

---

### Post by bodhi.zazen on 2010-08-31
> **alphacrucis2 said:**
> Are you meaning potential vulnerabilities in Wireshark's code? Surely the same risk exists with the linux kernel which you can't do anything about other than rely on such vulnerabilities being patched in a timely manner if they are discovered.

I am not understanding your point.

There are vulnerabilities in all code, kernel and otherwise. The vast majority of people here, on these forums, would rely on developers to patch code, kernel, wireshark, or otherwise.

A large part of linux security is running services / applications as much as possible as a non privileged user.

Kernel vulnerabilities are probably the worst in terms of impact to a system if exploited for a variety of reasons.

The potential of kernel vulnerabilities, IMO, is not a reason to run anything and everything as root and I would not advise logging in to a graphical desktop, firefox, wireshark, apache, etc as root as a matter of routine use.

---

### Post by alphacrucis2 on 2010-08-31
> **bodhi.zazen said:**
> I am not understanding your point.

There are vulnerabilities in all code, kernel and otherwise. The vast majority of people here, on these forums, would rely on developers to patch code, kernel, wireshark, or otherwise.

A large part of linux security is running services / applications as much as possible as a non privileged user.

Kernel vulnerabilities are probably the worst in terms of impact to a system if exploited for a variety of reasons.

The potential of kernel vulnerabilities, IMO, is not a reason to run anything and everything as root and I would not advise logging in to a graphical desktop, firefox, wireshark, apache, etc as root as a matter of routine use.

OK. I see what you mean.

---

### Post by bodhi.zazen on 2010-09-01
> **alphacrucis2 said:**
> OK. I see what you mean.

Sorry for any confusion, you brought up a good point, and I hope we all have a better understanding as a result.

---

### Post by Rubi1200 on 2010-09-01
> **Rumpletumbler said:**
> Thanks for the link. 

I found this [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/) and that explains it better than anything I've seen thus far.

Though still not entirely unconfused it makes a lot more sense.

I'm going to try it this way.
I pointed you to this link in post #5

---

### Post by Rumpletumbler on 2010-09-01
> **Rubi1200 said:**
> I pointed you to this link in post #5

I guess I missed it.

Your superior service didn't outshine my ignorance.

Thanks for your help.

---

