---
title: "VirtualBox OSE"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by hankaaron88 on 2010-08-18
If I install virtualbox ose do I need to install xp to run apps?

---

### Post by QIII on 2010-08-18
Yes.  You need to install an Operating System in a virtual machine -- just as you would on a physical machine.

---

### Post by hankaaron88 on 2010-08-18
Thanks. Does this work better than Wine?

---

### Post by TNT1 on 2010-08-18
> **hankaaron88 said:**
> Thanks. Does this work better than Wine?

Yes. IMO, it does. Your limitation with any VM is th eacatual physical hardware you run it on. I have a rather beefy machine, so it's not an issue for me. I would recommend you get the PUEL vbox though, so you can enjoy usb support.

---

### Post by QIII on 2010-08-18
You run Windows applications natively in Windows in a virtual machine.  Just as if it were on a physical machine.

You may be limited by the virtual hardware provided, however, so I don't know how well gaming would work.

The PEUL version is also available from [www.virtualbox.org](www.virtualbox.org).  You can add a software source and get updates when you do your normal updates.

PEUL version:  USB support but you can't use Virtual Network Computing.

OSE version:  No USB support but you can use VNC.

For most users, the USB support would be more desirable so I would recommend the PEUL version.

---

### Post by QIII on 2010-08-18
> **TNT1 said:**
> Yes. IMO, it does. 

There is little "opinion" about it.  Windows runs natively on the virtual machine, and Windows apps run natively in it.

Your physical hardware matters because you will be assigning some number of processor cores and memory to the VM.  However, the sound and graphics hardware is virtualized.

---

### Post by TNT1 on 2010-08-18
> **QIII said:**
> There is little "opinion" about it. 

I agree. I did once ask a similar question here, and received a ton of responses from each side, so I figured I'd word it opinion to play safe;)

---

### Post by bodhi.zazen on 2010-08-18
> **hankaaron88 said:**
> Thanks. Does this work better than Wine?

Depends on what you mean by better.

Wine is more secure (IMO).

Wine for "simple" applications such a utorrent or almost anything on potable apps is IMO better.

Virtualbox will work better for more complex applications.

Games are hit or miss with both options, wine is probably better.

---

### Post by TNT1 on 2010-08-18
> **bodhi.zazen said:**
> Depends on what you mean by better.

Wine is more secure (IMO).



Yeah, but if a vm gets corrupted in anyway, bin it and create a new one...

---

### Post by QIII on 2010-08-18
> **TNT1 said:**
> Yeah, but if a vm gets corrupted in anyway, bin it and create a new one...

Frequent snapshots.  Just back up to the last one.  Don't reinstall.

---

### Post by TNT1 on 2010-08-18
> **QIII said:**
> Frequent snapshots.  Just back up to the last one.  Don't reinstall.

yip. that works.

---

### Post by hankaaron88 on 2010-08-18
Thanks people. All I really want it for is to run ConvertX To DVD because I've tried DeVeDe, and ManDVD and didn't like either. Also, I tried ConvertX using Wine and it wouldn't work properly. Mainly it wouldn't recognize my DVD drive. But the advice is always appreciated.

---

