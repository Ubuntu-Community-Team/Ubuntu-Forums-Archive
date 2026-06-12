---
title: "Networking Help is needed, Probably simple."
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by savgen on 2008-02-05
Perhaps I'm retarded, but I cannot seem to get onto the internet.  Long story short, I had to install dapper to get ubuntu on my computer.  With all higher versions, the partition would crap out at 46%.  So, let it be known that I'm using dapper at the moment.

Now, I'd like to connect to the internet so that I can upgrade, but I can't seem to be able to do this.  This is my first time using ubuntu and I've about had it.  With all of the trouble I had simply getting this installed (about 10 different cds), I'm about ready to call it quits, but I figured that I would at least try these forums first.

I'm on a college campus.  My server (running ubuntu 7.10) installed and connected perfectly fine.  However, with this computer, nothing seems to work.  Any ideas?  (I really don't know how to set up internet connections, or even use ubuntu in the first place).

---

### Post by Dark Hornet on 2008-02-06
How many NIC's does your motherboard have?  One of my computers seems to have some issues with specific releases of Ubuntu because it has dual NIC's on the motherboard....just a thought.

---

### Post by savgen on 2008-02-06
this one has two, actually.  it recognizes both, but i only have one active.  the only ones that are up are eth0 and lo, and my cable is in eth0.

---

### Post by Dark Hornet on 2008-02-06
Yeah..don't misunderstand me, ALL versions of Ubuntu recognize both of the NIC's on the motherboard, only I think 7.04 will actually accept the DHCP address from the router, and assign it.  From what I have read, I think it is a bug with the chip set on my motherboard...its an ASUS A8n SLI....

---

### Post by savgen on 2008-02-06
Do you happen to know of a work around for it?

---

### Post by Dark Hornet on 2008-02-06
As of yet..no.  I am still working on the issue...once this issue is figured out, I will be able to uninstall XP from that machine and be able to proudly say that I do not own a MS OS...lol.

---

### Post by osos on 2008-02-06
which laptop do you have? do you connect wirelessly or through cable?

---

### Post by savgen on 2008-02-06
It's not a laptop, it's a desktop i built for myself.  The motherboard is:

[HTML]http://www.newegg.com/Product/Product.aspx?Item=N82E16813131074[/HTML]

so, actually, i'm not using a NIC, but I have built in dual-gigabit ports.  i believe the actual chipset for the ethernet is mcp55.  so, to answer your question, I'm wired.

---

### Post by osos on 2008-02-06
nice. open terminal and issue ipconfig. what's the output?

---

