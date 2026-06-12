---
title: "Showing over 4 GB of ram on 32-bit? That can't be right..."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Keir Azuma on 2010-08-22
During a reinstall I accidentally reinstalled my 32bit version of Ubuntu on my desktop which has 8GB of ram. When I look at my System Monitor, its shows all 8GB. This confuses me, as I thought 32bit systems only support around 4 GBs. 

Can anyone explain this?

Link: [http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png]("http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png")

---

### Post by sandyd on 2010-08-22
> **Keir Azuma said:**
> During a reinstall I accidentally reinstalled my 32bit version of Ubuntu on my desktop which has 8GB of ram. When I look at my System Monitor, its shows all 8GB. This confuses me, as I thought 32bit systems only support around 4 GBs. 

Can anyone explain this?

Link: [http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png](http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png)
yeah, I can. your using the PAE kernel.

---

### Post by Keir Azuma on 2010-08-22
Ah, that would explain it. Should I stick with the 32bit or correct my mistake and reinstall the 64bit?

---

### Post by Zzl1xndd on 2010-08-22
I would just stick with the 32 for now.

---

### Post by Keir Azuma on 2010-08-22
Sounds good to me. Thanks guys.

---

### Post by cascade9 on 2010-08-24
Almost everything that will benefit from 8GB of RAM will also benefit from 64bit. 

I'd change to 64bit myself, for that reason, and because if your computer is capable of 64bit, why not use it?

---

### Post by phillw on 2010-08-24
> **cascade9 said:**
> Almost everything that will benefit from 8GB of RAM will also benefit from 64bit. 

I'd change to 64bit myself, for that reason, and because if your computer is capable of 64bit, why not use it?

Read above ;)  Unless you **need** a programme that runs only in 64 Bit mode, using the 32 Bit kernel with PAE should not give you any large speed difference; put along with negating any issues with incompatibility. It is why they spent the time developing PAE.

Regards,

Phill.

---

### Post by cascade9 on 2010-08-30
> **phillw said:**
> Read above ;)  Unless you **need** a programme that runs only in 64 Bit mode, using the 32 Bit kernel with PAE should not give you any large speed difference; put along with negating any issues with incompatibility. It is why they spent the time developing PAE.

PAE might be able to use more RAM than normal 32bit, but if you are doing any hard number crunching, PAE gets left in the dust- 

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by philinux on 2010-08-30
> **Keir Azuma said:**
> During a reinstall I accidentally reinstalled my 32bit version of Ubuntu on my desktop which has 8GB of ram. When I look at my System Monitor, its shows all 8GB. This confuses me, as I thought 32bit systems only support around 4 GBs. 

Can anyone explain this?

Link: [http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png]("http://dl.dropbox.com/u/1258410/Screenshot-System%20Monitor.png")

[32-bit-vs-64-bit-benchmarks]("http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks")

---

### Post by jerome1232 on 2010-08-30
And the can of worms has been opened. To each his own but....

My opinion is, 


64 bit! The issues that still exist with 64 bit are few and far between. Plus hard number crunching is flat out faster under 64 bit, I don't think the average user realizes how much encode/decoding, compression/decompression, or sometimes even encryption/decryption is done during our normal day to day tasks.

---

### Post by QIII on 2010-08-30
Does anyone remember the question "Why should I switch to 32 bit?"

---

