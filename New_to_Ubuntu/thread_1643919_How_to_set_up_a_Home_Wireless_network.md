---
title: "How to set up a Home Wireless network"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by cpcpcp on 2010-12-12
I have a couple of Ububtu machines and a radio connecting OK to the internet through the wireless modem supplied by my ISP. What do I need to buy (if anything) so that they can all see each other wirelessly and share files (music etc)?

 I think I need to buy a wireless router - is this correct or can I do something clever with the wireless USB dongle in my main machine?
The wireless routers I looked at seem to need a microsoft running machine for the initial set up is this true? The main machine is dual boot (to Vista) if that helps.

If you suggest buying a an ABC or model XYZ router thingy or even a Wireless modem router thingy please bear in mind I am in the UK - and if there is simple cheap option that would be my favourite.

[B]So in essence what hardware (if any) do I need and then what?

[/B]I also want to buy a wireless printer at a later date.

---

### Post by ajgreeny on 2010-12-12
Are you certain that your "wireless modem" is not actually a router?  Can all three machines connect to it at the same time?  If so I think it is a router and you don't need anything more.

I have no idea how you can connect from ubuntu to a radio on the network but it is easy to setup a connection between the two ubuntu machines using either ssh or NFS, probably the latter if you want them always connected.

I use ssh for the machines in my household, but only connect them when I need to, which is sometimes only once or twice a month, and have the sshd daemon not start by default on all machines, and start it when needed with an alias in terminal.  This gives me greater security, and means there is no ssh server running unless I start it.

If you want more info, ask again about ssh.  I can't help with NFS as I have never used it.

---

### Post by cpcpcp on 2010-12-13
> **ajgreeny said:**
> Are you certain that your "wireless modem" is not actually a router?  Can all three machines connect to it at the same time?  If so I think it is a router and you don't need anything more.

I have no idea how you can connect from ubuntu to a radio on the network but it is easy to setup a connection between the two ubuntu machines using either ssh or NFS, probably the latter if you want them always connected.

I use ssh for the machines in my household, but only connect them when I need to, which is sometimes only once or twice a month, and have the sshd daemon not start by default on all machines, and start it when needed with an alias in terminal.  This gives me greater security, and means there is no ssh server running unless I start it.

If you want more info, ask again about ssh.  I can't help with NFS as I have never used it.
It is a wireless modem - apparently capable of serving up to 224 machines (but at what speed I would hesitate to guess)

---

### Post by ajgreeny on 2010-12-13
> **cpcpcp said:**
> It is a wireless modem - apparently capable of serving up to 224 machines (but at what speed I would hesitate to guess)
I didn't know such things existed!  I also think you will therefore need a wireless router in order to use either ssh or NFS.

---

### Post by alphacrucis2 on 2010-12-13
> **cpcpcp said:**
> It is a wireless modem - apparently capable of serving up to 224 machines (but at what speed I would hesitate to guess)


Do you have a make and model number?

---

### Post by cpcpcp on 2010-12-13
It is called a BE Box - it is actually made by thompson a TG585 v7
[https://avatar.bethere.co.uk/html/BeBox_Manual/TG585-v7_en/wwhelp/wwhimpl/js/html/wwhelp.htm?single=false&context=sug&topic=init](https://avatar.bethere.co.uk/html/BeBox_Manual/TG585-v7_en/wwhelp/wwhimpl/js/html/wwhelp.htm?single=false&context=sug&topic=init)

---

### Post by wep940 on 2010-12-13
Just briefly scanning the manual online at the link you gave, and looking at the drawing in section 3, it appears this is a DSL Modem and router.  You appear to have 3 ports you can hard wire to, and the rest is wireless.  They are calling it a gateway mainly because it is combining the modem and router in 1.  Normal procedures for setting up a home network should still apply.

---

### Post by cpcpcp on 2010-12-14
> **wep940 said:**
> Just briefly scanning the manual online at the link you gave, and looking at the drawing in section 3, it appears this is a DSL Modem and router.  You appear to have 3 ports you can hard wire to, and the rest is wireless.  They are calling it a gateway mainly because it is combining the modem and router in 1.  Normal procedures for setting up a home network should still apply.

I think you are right.
**And Apologies to ajgreeny**

This is what they have just written to me
*"Thank you for the update.   The Be Box is a Modem with Wireless functions. So this means it acts as a  modem with a Built in Wireless router. In order to get your machines to  connect one to each other in your internal network, you will need to  share properly the connection from your operating system's settings.  Unfortunately since this is a third party software, and we cannot  support such services, you will need to check the guides in your  operational systems' manufacturers website.   You can share the connection between the computers, you just need the  right settings on them, not on the be Box.*"

So I guess it comes down to my second question, in simple terms if you would be so kind people,

**What steps must I follow ?**

---

### Post by cpcpcp on 2010-12-20
> **cpcpcp said:**
> I think you are right.
**And Apologies to ajgreeny**

So I guess it comes down to my second question, in simple terms if you would be so kind people,

**What steps must I follow ?**

Well no one has come back at me.
So far I have installer  SSH on one machine as a server (at least I think I have)

I get this but I do do not understand what I ought to do.(here is a screen shot to do with personal files sharing  )

[IMG]file:///home/cjp/Desktop/Screenshot-Personal%20File%20Sharing%20Preferences.png[/IMG]

---

