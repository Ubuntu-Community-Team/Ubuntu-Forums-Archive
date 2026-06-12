---
title: "Help me convert my clients to Ubuntu plz - remote help under this OS?"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by sindyr on 2008-03-20
I currently have many clients (I am a computer consultant) who are basic email/browser/word processor users.  Many of this clients might be better served by Ubuntu, rather than the joy (sarcasm intended) of Windows or Mac.

However, I now have two tools to be able to help my clients when they get into a jam.

My best tool is techinline.com.  I pay a small fee (15$/month), and all I do is send my clients to a simple web site, and two clicks later they have a 6 digit pin code to give me, which is all I need to log into their machine and help them immediately.  I am able to see and control the machine completely - and they don't have to worry about waiting until my next scheduled appointment opening nor do they have to pay my emergency rates.

Another simple tool I have is logmein.com - with a simple install I can log into their machine anytime I need to.  But techinline is the better tool for getting into a client's machine without warning or preinstallaion.  Of course, I can use techinline to install logmein, and have.

The point is, these clients are NOT geeks.  I cannot lead them though a spontaneous installation of VNC.  I can't ask them to follow my directions in editing their router to forward ports, or get their IP address.  I need a *SIMPLE* solution that requires at most a few clicks.

Is there ANYTHING possible like this under Ubuntu?  I am not opposed to a 10-15$ all in monthly subscription.

If not, is there a super simple pre-installation I can do when first setting up their Ubuntu PC that would enable me to see and control their computer without knowing what their IP address is?  Again, this has to be a super simple (for them) setup with no per user charge.

The truth is, all I find that people are talking about on these boards is VNX and FreeNX, neither of which to the best of my knowledge works well when operating across the internet (and not a local net) and with clients that do not want to be part of the process.

Any ideas?

---

### Post by JawsThemeSwimming428 on 2008-03-20
Don't know if this would help you out or not but I use NXNomachine. It is an SSH client that works pretty well. I think there are ways to get it working to kind of what you want.

---

### Post by sindyr on 2008-03-20
Ah - sorry, I should have mentioned that the control and view of the box I want to have is the GUI/X-Win view that my clients are seeing.

In other words, I want to be using their computer as if I was sitting in front of it.

So I don't think SSH or telnet will fit that bill, unless you get GUI control of the machine somehow using it?

Thanks.

---

### Post by MikeyXX on 2008-03-20
Hopefully being a network/computer consultant you appreciate that there is a two fold problem.

 They are behind a router of some sort so getting to there machines will require a path that has been determined. I don't think you want to make a firewall rule for each of your clients so you need more than just remote software.

So perhaps, what you are looking for is a logmein type client for Linux as appose to a VNC type solution. Correct?

I don't have that answer, but I'm interested as well.

---

### Post by sindyr on 2008-03-20
> **MikeyXX said:**
> Hopefully being a network/computer consultant you appreciate that there is a two fold problem.

 They are behind a router of some sort so getting to there machines will require a path that has been determined. I don't think you want to make a firewall rule for each of your clients so you need more than just remote software.

So perhaps, what you are looking for is a logmein type client for Linux as appose to a VNC type solution. Correct?

I don't have that answer, but I'm interested as well.

Exactly so - I am open to any solution, but the only one I can imagine doing the trick is something like techinline or logmein under Ubuntu.

---

### Post by drdos2006 on 2008-03-21
Once you have Hamachi ( LogMeIn ) installed, cant you run VNC over Hamachi ?

regards

---

### Post by sindyr on 2008-03-21
Hamachi + VNC seems inelegant and a little plain box/basic, but its about the only thing that will probably come close that's available for linux.

I guess I was hoping for a more... commercial solution - but in my heart, I knew that most commercial solutions are only for Windows (and Mac).

Thanks anyways guys - if anyone knows of any other method, let me know, but I think Hmachi and VNC is probably the best we will do.

---

### Post by wormser on 2008-03-21
This is EXACTLY why I suggested [Desktop Sharing]("http://ubuntuforums.org/search.php?searchid=38148563") (aka OS X Screen Sharing).  I have no idea why it has not gained support.  It is a killer app that every other OS has adopted.  If you see the need for it post on the link.

Vote for it here:  [http://brainstorm.ubuntu.com/idea/7487/](http://brainstorm.ubuntu.com/idea/7487/)

---

