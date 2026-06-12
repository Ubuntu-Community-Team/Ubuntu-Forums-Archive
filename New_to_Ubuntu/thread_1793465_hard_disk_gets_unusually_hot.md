---
title: "hard disk gets unusually hot"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by HKGautam on 2011-06-29
hello
i have installed ubuntu 11.04 along with windows 7.I have noticed that while using ubuntu ,hard disk becomes unusually hot.Is there any setting to be made to correct this problem?
Thank you

---

### Post by LowSky on 2011-06-29
Hi welcome to the forums.

Define Hot? And why are you feeling up the hard disk when your using it?

---

### Post by amjjawad on 2011-06-29
Hello and Welcome :)

HDD usually becomes hot whether you install Ubuntu or any other OS but as our friend here asked you to define hot and how hot is it?

I recall there is an application you install to check the temp of the HDD but not sure how accurate it's.

---

### Post by pqwoerituytrueiwoq on 2011-06-29
> **amjjawad said:**
> Hello and Welcome :)

HDD usually becomes hot whether you install Ubuntu or any other OS but as our friend here asked you to define hot and how hot is it?

I recall there is an application you install to check the temp of the HDD but not sure how accurate it's.
hddtemp
also you may want the sensors-applet my hdd is at 28/29 C about the same as my cpu on idle

---

### Post by amjjawad on 2011-06-29
> **pqwoerituytrueiwoq said:**
> hddtemp
also you may want the sensors-applet my hdd is at 28/29 C about the same as my cpu on idle

Yes, thanks for the reminder :)

Last time I used it, my HDD's temp was 40c.

---

### Post by Mark Phelps on 2011-06-29
Unless you're montoring HDD temps (and you didn't say you are), then I'm guessing this is a laptop and you're feeling it get a lot warmer then when running Win7.

It's unlikely that this is due to the HDD running warmer (since Ubuntu is likely to use less disk activity than Win7), but more likely, due to your CPU not scaling back when idle in Ubuntu -- a problem that lots of folks have reported with 11.04.

One way you can tell is listening to the CPU Fan. If it's running a LOT in Ubuntu but not in Win7, that means your CPU is running hotter in Ubuntu -- and that is heating up your laptop case.

---

### Post by HKGautam on 2011-07-04
Thank you all for replying and sorry that i didnt reply back sooner.
I say hard disk is hot because i have checked it at disk utility.
The reading says it is 50 degree.I was a little worried because temperatures never went beyond 41 while using windows. I installed the proprietary graphics driver for ATI card.Now disk temperature reads 49 degrees.I dont run any resource intensive application.
I forgot to tell that i use a laptop. 
I couldnt tell if fan is running more in ubuntu.I feel it is about the same but not sure.The computer feels unusually hot only in hard disk section.
Is the temperature bad for hard disk?
I fear that using the computer for long time is bad for hard disk.

---

### Post by amjjawad on 2011-07-04
Heat is bad for such devices. Perhaps you need extra fan or something ... forgot what's the name of that thing :(

---

### Post by HKGautam on 2011-07-04
Thanks
so it is not some software issue?
is it possible to install additional fans to laptop?Are they very expensive?
i also came across term load cycle count.after use for 3389 Hr ,the count stands 105602.The count dose not increase very much.I have heard this parameter is also related to hard disk .But the more i read about it more i get confused and i am nowhere near solving the heating problem.

---

### Post by amjjawad on 2011-07-04
> **HKGautam said:**
> Thanks
so it is not some software issue?
is it possible to install additional fans to laptop?Are they very expensive?
I don't think so.
I'm using HP Pavilion DV6 (Core i5 - 4GB RAM - 1GB ATI) with Windows 7 and sometimes it's SO HOT. However, I'm not using it for long hours so I don't need to buy any extra thing for it.

I forgot what's the name of that device? it's like a dock where you can put your laptop on with some fans. My brother have one but he's not online so can't ask him now. We live in two different countries.
I don't think it's expensive.

Wait, there you go: [http://www.google.com/search?q=dock+fan+for+laptops&hl=en&client=ubuntu&hs=5wR&channel=fs&biw=1152&bih=649&prmd=ivns&source=lnms&tbm=isch&ei=TOURTuDHF8HMrQeb1uHJBg&sa=X&oi=mode_link&ct=mode&cd=2&ved=0CBQQ_AUoAQ](http://www.google.com/search?q=dock+fan+for+laptops&hl=en&client=ubuntu&hs=5wR&channel=fs&biw=1152&bih=649&prmd=ivns&source=lnms&tbm=isch&ei=TOURTuDHF8HMrQeb1uHJBg&sa=X&oi=mode_link&ct=mode&cd=2&ved=0CBQQ_AUoAQ)

---

### Post by Mark Phelps on 2011-07-04
OK ... so it is actually the HDD that is running hot. Is that temp "F" (fahrenheit) or "C" (centigrade)? 

If that is "F", that is actually running rather cool.  If it's "C", then that is very hot (around 122).  Asking because I have a laptop whose old HDD use to run up to 120 "F" on a regular basis.  Kept setting off the temp monitor I had set for the drive!

Replaced it with a newer HDD and now, it almost never exceeds 100 "F" (about 38 "C").

---

### Post by amjjawad on 2011-07-04
> **Mark Phelps said:**
> Replaced it with a newer HDD and now, it almost never exceeds 100 "F" (about 38 "C").

I think the normal temperature for HDD is around 40c.

---

### Post by CajunPirate on 2011-07-04
Shot in the dark but worth a look: Check the laptop manufacturer's website for BIOS updates. I had the same problem and found a BIOS update that fixed a fan error.

---

### Post by wildmanne39 on 2011-07-05
Hi, I have a laptop that runs hot when using many applications but I bought a chilling pad with fans to put it on for about twenty dollars and it cooled it down twenty degrees, it also helps to clean them out. Here is a link for cooling of laptops.
[http://ubuntuforums.org/showthread.php?p=10821788#post10821788](http://ubuntuforums.org/showthread.php?p=10821788#post10821788)

---

### Post by HKGautam on 2011-07-05
Thanks again
The temperature is in centigrade.
I have updated the bios to the latest version available.My laptop is year and half old.it is an inspiron 1440 model.
hard disk is 320gb western digital Scorpio blue.
It was mentioned in one of the post that CPU heating may be the reason.could you elaborate on it?
Can i safely use the computer with HDD temperature around .
could you please tell me the temperature of your HDD while using ubuntu.

---

