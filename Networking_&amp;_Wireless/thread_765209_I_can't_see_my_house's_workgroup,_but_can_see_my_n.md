---
title: "I can't see my house's workgroup, but can see my neighbor's!"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by andrebrait on 2008-04-24
Hi

I have Ubuntu 8.04 x86-64 here and got a problem. I never tried with other versions, so I don't know if it's a hardy specific problem. 

When I go to Places > Network, there's an Icon called "Windows Network"

I can see my neighbor's network. He's connect in my router through Wireless.
But I can't see my own network! I have two computers here. The other one is turned on and uses XP Pro SP2, just like my neighbor, but I can't see my network!

---

### Post by Swiftfeet8 on 2008-04-24
Can your neighbor see your network?  If not I would verify that your second computer is on the correct workgroup.  Although I believe if it wasn't you would still see it show up in ubuntu under whatever workgroup it is part of.  

Can you reach your second computer by pinging it?  If you can ping it I would check to see if there is some security in place that doesn't allow you to see it on your network.

Let me know if any of this helps or doesn't help and I will try to help you some more...(man that was a lot of help's :))

---

### Post by andrebrait on 2008-04-24
Yes, I can ping it.

Me and my neighbor are in different workgroups
Me and My second computer are in "Grupo", and He's in "Teruah".
When I Open the Network, I see Windows network. When I Open it, I should see the workgroups, but I can only se his workgroup, Teruah!
When I double-click Teruah, i see his computer, called CASEMOD, and so his shares.

My own workgroup is not present!
I'll try it again... restarting everything, including the router.

Btw, how can i share folders with Windows PCs?

---

### Post by Swiftfeet8 on 2008-04-24
In order to share folders with Windows PC's you need to have Samba installed.  Below is a link to a how-to on setting up shares in Ubuntu.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

What is the workgroup that your Ubuntu computer is part of?  If you go through the how-to above for setting up Samba it may resolve the issues that you are currently having with your house workgroup.  Let me know if it doesn't.

---

### Post by andrebrait on 2008-04-24
I'll try it later
Currently, when I tried to see other Computers with my Windows PC, it gave me an error saying it couldn't connect to the group "Grupo", instead of showing only itself or an empty group, as expected.

I'm trying to configure it through the assistant...

SUCESS!!

It seems it was only being part of the group, not hosting the group too.

Now everything is fine =D

I'll try samba, thanks! ^^

---

### Post by andrebrait on 2008-04-24
I'll try it later
Currently, when I tried to see other Computers with my Windows PC, it gave me an error saying it couldn't connect to the group "Grupo", instead of showing only itself or an empty group, as expected.

I'm trying to configure it through the assistant...

SUCESS!!

It seems it was only being part of the group, not hosting the group too.

Now everything is fine =D

I'll try samba, thanks! ^^

---

### Post by Swiftfeet8 on 2008-04-24
Cool, glad it's working.  Let me know if you have troubles setting up Samba.

---

### Post by andrebrait on 2008-04-24
No... it stopped working

When I click the other computer shares, it asks me for password... what password?
In Windows I can acess them without any password!

Now I can't even see its shares... I'll try rebooting both computers...

---

### Post by andrebrait on 2008-04-24
bump

---

