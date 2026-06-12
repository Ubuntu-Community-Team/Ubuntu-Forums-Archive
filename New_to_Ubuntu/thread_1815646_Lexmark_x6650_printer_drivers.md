---
title: "Lexmark x6650 printer drivers"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-07-31
I've just downloaded the print drivers for my Lexmark x6650 (See: [http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_X6650&segment=SUPPORT&userlocale=EN_US&frompage=null#1](http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_X6650&segment=SUPPORT&userlocale=EN_US&frompage=null#1)) but when it asks for my admin password it states that I'm entering the wrong password. I've double checked the caps locks and numb locks and both are off/on respectively. Any ideas on what to do?

---

### Post by wojox on 2011-07-31
Same here a while back. Run the script as "sudo". It will ask for your password right away instead of through the script. :P

---

### Post by JacquesPotter on 2011-07-31
OK how do I run it as "sudo"? I'm really new to this stuff. Can you give me a step by step?

---

### Post by wojox on 2011-07-31
Open a terminal and cd to the directory you downloaded it.

You unpacked it already?

```
tar -xzvf lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```

```
sudo sh lexmark-08z-series-driver-1.0-1.i386.deb.sh
```

---

### Post by JacquesPotter on 2011-07-31
Not sure? What is unpacked? I opened it and then extracted it if that's what you mean.

---

### Post by wojox on 2011-07-31
> **JacquesPotter said:**
> Not sure? What is unpacked? I opened it and then extracted it if that's what you mean.

That's what I mean. Where is it? On the Desktop, in Downloads?

---

### Post by JacquesPotter on 2011-07-31
OK I entered the code tar: lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
but then I get this:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Does that mean that I haven't unpacked it yet?

---

### Post by JacquesPotter on 2011-07-31
> **wojox said:**
> That's what I mean. Where is it? On the Desktop, in Downloads?
I put right onto my desktop.

---

### Post by wojox on 2011-07-31
> **JacquesPotter said:**
> OK I entered the code tar: lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
but then I get this:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Does that mean that I haven't unpacked it yet?

Well it would unpack if again. I have a feeling your not in the right directory?

---

### Post by wojox on 2011-07-31
> **JacquesPotter said:**
> No I wasn't sure where to put it so I put right onto my desktop.

Okay. Open a terminal and type:

```
cd Desktop
```

```
ls -al
```

Post back the ls -al part.

---

### Post by JacquesPotter on 2011-07-31
Ok, I've done that and a long list erupted. what next?

---

### Post by wojox on 2011-07-31
Is there anything that resembles lexmark-08z-series-driver?

---

### Post by JacquesPotter on 2011-07-31
Not that I can tell. Am I looking for something specific other then the  "lexmark-08z-series-driver"?

---

### Post by wojox on 2011-07-31
What does this output:

```
la -al | grep lexmark
```

---

### Post by JacquesPotter on 2011-07-31
Nothing. I can see and access the Lexmark icon on the desktop if this helps.

---

### Post by wojox on 2011-07-31
Alright. Let's go this route. In the terminal type:

```
gksudo nautilus
```

It will ask for your password and open your file manager in root.

Be careful.

Look on the left hand side and click on Desktop and them the lexmark icon then run the script.

---

### Post by JacquesPotter on 2011-07-31
> **wojox said:**
> Alright. Let's go this route. In the terminal type:

```
gksudo nautilus
```

It will ask for your password and open your file manager in root.

Be careful.

Look on the left hand side and click on Desktop and them the lexmark icon then run the script.

OK, there's something seriously wrong. Lexmark isn't even in there. Do I need to re-install it and be sure that it's on my desktop? The weird part is that it is on my actual desktop and I can access it from there.

---

### Post by dcsoldschool53 on 2011-08-01
> **wojox said:**
> Alright. Let's go this route. In the terminal type:

```
gksudo nautilus
```It will ask for your password and open your file manager in root.

Be careful.

Look on the left hand side and click on Desktop and them the lexmark icon then run the script.
  No, if he click on desktop on the left hand side, it will take him to the root desktop. This is not where he needs to be. Try this in a terminal to get to the right desktop where you need to be```
gksudo nautilus ~/Desktop
```It will ask for password, and open up nautilus in your home directory's Desktop. You will now see the Lemark tar.gz file, sitting where you had left it

---

### Post by JacquesPotter on 2011-08-01
> **dcsoldschool53 said:**
> No, if he click on desktop on the left hand side, it will take him to the root desktop. This is not where he needs to be. Try this in a terminal to get to the right desktop where you need to be```
gksudo nautilus ~/Desktop
```It will ask for password, and open up nautilus in your home directory's Desktop. You will now see the Lemark tar.gz file, sitting where you had left it

Excellent. That worked. Thank you so very much!!!

Thanks to both of you actually. It was a learning experience that will help me in the future as a well. I greatly appreciate being able to print again!!!!!

---

