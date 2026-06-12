---
title: "Linux Kernel Image ?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Kensoi on 2009-04-27
Hi. Still Very Much New To Ubuntu.

I Noticed This (Please See 1st Screenshot) 
I Have Been Told That Gufw Is The One We Should Be Using Altho I Have Been Having Problems With That Also Failing To Stop Traffic When Asked !

So I Put Firestarter Back  On Thinking Everything Was Fine.
I Could Stop Traffic If I Needed To & Connections Showing Etc.

Me Being New I Am Now Exploring The File System Etc & That Is Where I Found The Ist Screenshot. So Looking Around I Discovered The Kernel Does Not Have A Ubuntu Logo Next To It (Please See Second Screenshot)Is This Ok ?

Basically I Would Appreciate Any Help Regarding The Above. . 

Thanks
       Ken

---

### Post by LowSky on 2009-04-27
the logo only means that the package is developed/mantained by the ubuntu staff. If it doesn't have the logo then its maintained by another group.

It doesn't mean it isn't safe, it just means its not updated by the Ubuntu group. Plenty of applications are safe to run, including the kernel if needed.

---

### Post by Kensoi on 2009-04-27
Thanks For That. I Had Wondered About The Logos.

So Does Anybody Have Any Ideas On Why The Logging Is Not Supported By The Kernel & Not Allowing Events To Show Up ?

---

### Post by tarps87 on 2009-04-27
Looking at the second screen shot it appears you are using a kernel customised for the netboot or netboo ;)
Although this is not developed by the Ubuntu devs, I believe it is branched of the latest kernel Ubuntu uses. You should be ok using it.

---

### Post by tarps87 on 2009-04-27
Could you let us know the name of the file. When do you see the error message?

---

### Post by Kensoi on 2009-04-27
Thanks. 

The Name Of The File Is FIREWALL Inside The Firestarter FOLDER Which is Inside The ETC FILE In FILE SYSTEM.

Ken

---

### Post by tarps87 on 2009-04-27
That will be part of firestater, if you start fierstarter through the terminal to you see the error message?

---

### Post by Kensoi on 2009-04-27
Can You Tell Me What Command That Is ? Thanks.

Don't Use Commands In The Terminal Often.

Do You Mean Firestarter Status ? From The Terminal.

If You Do It Starts Firestarter.

---

### Post by tarps87 on 2009-04-28
I can't remember the command but I think it is just firestarter, I will have to check. If you can start firestarter without and you don't see the error message then there kernel does support logging. Can you let me know what version of Ubuntu you are using so I can test it? It seems to work on Ibex but I'm not using the netbook kernel

---

### Post by Kensoi on 2009-04-28
8.04 Hardy Heron.

When Using Firestarter From The Terminal It Starts It.

The Problem Is How Do You Know If The Events Section Is Working?

I Suppose Going Into A Public Wi Fi Spot Would Tell Me ?

---

### Post by tarps87 on 2009-04-28
On the basis that you don't see any error messages you can assume it is supported and working. Other than that you would have to test it using different scenarios. The file you are looking at is just a script used to check if the features are supported, it is not a log file. Also I think I should make it clear that the firewall you are using is called IPtables, firestarter is just a GUI for configuring a monitoring the firewall.

Hope this helps

---

### Post by Kensoi on 2009-04-28
Thanks For That. I Do Realise About iptables Etc. Didn't Realise About The Script.

I Suppose In Someways I'm Still In xp Mode. 

Ubuntu Is A Very Steep Learning Curve For Me. I'm Not From A Computer Technical Background. So I'll Just Need To Stay With It & Hope It Makes Sense. There Seems To Be Alot Of Conflicting Points About Firewalls & GUI.

Which Seems To Make It Harder To Understand At Times.

Thanks 
        Ken

---

