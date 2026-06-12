---
title: "USB internet providers for Linux"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by craig1976 on 2010-03-06
Hi

I live in America and I'm trying to find a internet service provider that will allow me to access the internet through a mobile USB stick.

I've had no luck so far. I've tried Clear but they are not Linux compatible.

I'm running Ubuntu Hardy Heron (fully up to date).

Thanks for your time.

Craig

---

### Post by ikt on 2010-03-06
Have you tried running a live cd of 9.10?

---

### Post by wojox on 2010-03-06
There's Sprint and Verizion.

---

### Post by Mark Phelps on 2010-03-08
By accessing the Internet through USB, I take it you mean using a USB wireless device?

If that's so, look at the link below for ISPs that allow wireless access:

[http://wireless.theispguide.com/findcitystate.asp]("http://wireless.theispguide.com/findcitystate.asp")

---

### Post by craig1976 on 2010-03-11
Sorry, yes - just worded it wrong.

Thank you for the help everyone.

I'm still searching. Sprint haven't got back to me about compatibility yet.

Does anyone know if Cricket mobile wireless is compatible with Ubuntu Linux? 

cheers

Craig

---

### Post by 3rdalbum on 2010-03-11
Usually, the issue is the modem that the ISP provides. Some modems have drivers built into the kernel, some don't. Your best bet is to ask the prospective ISP what modem they provide, and then look at compatibility yourself. They will all answer: "We don't support Linux", even if their modems and service work perfectly on Ubuntu.

Your biggest concern at the moment will be the age of your distribution. Ubuntu 8.04's version of Network Manager is too old to support mobile broadband. Some modems can be made to work, but it's tough and requires a lot of hacking around... not worth it.

Ubuntus 8.10 and above support mobile broadband out-of-the-box.

In short, check the model numbers of the modems that these ISPs provide, and upgrade your version of Ubuntu (preferably not to 9.10, it has issues with mobile broadband). If you want to stick with an LTS release, try installing Alpha 3 of Ubuntu 10.04, which will be an LTS when it is released next month.

---

### Post by monthos on 2010-03-16
Its been awhile, but I know my cricket air cards work in ubuntu. The first activations and all were done on windows (including *228 which gets the newest PRL, which updates software for roaming/new markets). But afterwards I put them on many ubuntu boxes without issue.

insert aircard, ubuntu should detect it as a usb serial device, then I just set up a ppp connection, tell it to dial #777, and I think no username or password, if it complains try the username as the MDN(phone number) of the aircard with no password.

This has worked for me when my cable died. I have not used by aircard for many months now but I see no reason why it wouldnt still, I only use it when I need to VPN in on the road or my cable dies at home.

---

