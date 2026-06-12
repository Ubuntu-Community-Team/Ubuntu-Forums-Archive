---
title: "[SOLVED] Evolution causes full crash needing hard reset"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by mac98aop on 2008-12-02
Hi


Now and again, (no rhyme nor reason) Evolution just freezes the whole machine. No key commands Force Quit or anything, it requires a hard reset.

Any ideas?

Trouble is, I'm only a week into Ubuntu on a Dell Mini 9. I'm loving it but any technical answer might be a bit advanced! If anyone could kindly help but explain any steps I need to take (ie, telling me what to type in the Terminal but not explaining what it does is terrifying!) would be greatly appreciated!

I'm running 8.04 (Dell install on Mini 9) in the Ubuntu desktop configuration. I have installed compiz-fusion to make things look nicer too. Could that be it? Although even in Metacity it crashes.

Thanks

---

### Post by Titan8990 on 2008-12-02
Evolution is not very good IMO. I wouldn't take the time to troubleshoot the issue. I would just move on to something better:


Applications -> Accessories -> Terminal -> Input the following:

sudo apt-get install thunderbird thunderbird-gnome-support

---

### Post by mac98aop on 2008-12-02
Ok!

So, why is not very good? Please expand.

Further, does what you suggest install Thunderbird? Could I also look in Synaptic? Or download from their website?

Is it better to install from the Command Line? Does it pull the download from Mozilla?

Sorry for all the Qs but I'm loving Ubuntu thus far and so keen to understand more....

---

### Post by Titan8990 on 2008-12-02
Well, I have had many issues in Evolution with sending and receiving timing out. I usually have to cancel and do it again or wait for the timeout. My switch to thunderbird resolved the issue. Although Evolution does have some nice features such as the ability to probe a server for authentication methods.

> 
Further, does what you suggest install Thunderbird? Could I also look in Synaptic? Or download from their website?

Is it better to install from the Command Line? Does it pull the download from Mozilla?

Yes, that will download and install Mozilla Thunderbird. You could look in Synaptic if that is what you prefer. I don't recommend getting it from their website unless they have a .deb package. Usually you will only download and install from a website if the copy in the Synaptic Package Manager is too out of date for use (I have never ran in to that problem).


Installing from CLI and Synaptic is the same. Most support you will get from the forums will be in CLI and that is what most of the people that help use. Not only that but I personally find it easier to instruct you to copy and paste one line as opposed to multiple clicks, etc.

---

### Post by halitech on 2008-12-02
I've never had a problem with Evolution, it even syncs with my old Palm m105. I also use Thunderbird and find it a tad faster then Evolution.

---

### Post by mac98aop on 2008-12-02
I can't believe this..... I have posted a question and within minutes have help! SO SO GRATEFUL! 

Ok, so I've not had time yet to see if it resolves the issue but either way - it's a great start!

Thanks again!

Anyone else got any thoughts on Evolution?

---

### Post by mac98aop on 2008-12-02
> **halitech said:**
> I've never had a problem with Evolution, it even syncs with my old Palm m105. I also use Thunderbird and find it a tad faster then Evolution.

So any ideas why it might be crashing!?!? Causing full system crash!! I thought Ubuntu was ultra stable!!

---

### Post by Titan8990 on 2008-12-02
> So any ideas why it might be crashing!?!? Causing full system crash!! I thought Ubuntu was ultra stable!!

Only if you hardware is fully compatible....


If it is only one program, I wouldn't be concerned. If it begin happening in other things, then we can look at your system logs.

---

### Post by mac98aop on 2008-12-02
> **Titan8990 said:**
> Only if you hardware is fully compatible....


If it is only one program, I wouldn't be concerned. If it begin happening in other things, then we can look at your system logs.

Great. I did Google the issue before joining the forum and is it fair to say that others have experienced trouble with Evolution and IMAP? No real specifics but it seems others have reported crashes when it is set up for IMAP access...

---

### Post by halitech on 2008-12-02
I've never used IMAP so no idea if that might be causing it. Linux by design is stable but you have to take into account the hardware its running on, restricted drivers you have enabled and any other software that you have installed or updated.

---

### Post by mac98aop on 2008-12-02
> **halitech said:**
> I've never used IMAP so no idea if that might be causing it. Linux by design is stable but you have to take into account the hardware its running on, restricted drivers you have enabled and any other software that you have installed or updated.

Ok, so could python-compizconfig have done it?
Or, compiz-fusion?

Secondly, how do I know which window manager I'm using? People talk of emerald, GTK etc?

---

### Post by halitech on 2008-12-02
add ons like compiz can cause some strange things to happen. try disabling any that you are using and see if Evolution still crashes.

---

### Post by Titan8990 on 2008-12-02
Agreed, Compiz is really nice but it does take hit in the stability area, especially with full screen applications like games.

---

