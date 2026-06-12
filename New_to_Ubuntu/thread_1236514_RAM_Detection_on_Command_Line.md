---
title: "RAM Detection on Command Line?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-08-10
Hey all.  I'm looking to install a RAM upgrade into my laptop, even though I probably shouldn't...  I'm in just a little over my head digging around in a computer, but I know the risks and am up for a challenge.

I couldn't find my RAM cards in my laptop when I was poking around the other day.  Is there a command line prompt that can detect what kind of RAM I'm using (DDR, DDR2, etc.) and how much RAM it has in MB/GB/etc?

I'm hoping that once I get the RAM card I'll be able to find a chip that looks like it in my computer and locate my existing RAM card that way. ^^;

---

### Post by Narada on 2009-08-10
RAM in laptops is noticably smaller than it is in desktops. That may help you in your search. As for a command line utility I don't know of one that tells you your actual RAM specifications, but if you run "top" you can view your total installed memory.

---

### Post by Revolutionary101 on 2009-08-10
This command should give you all the information you need.

```
sudo dmidecode –type 6
```

---

### Post by unutbu on 2009-08-10
To find how much RAM you current have, you could open a terminal (Applications>Accessories>Terminal) and type

```
% free -m
             total       used       free     shared    buffers     cached
Mem:          **1007**        937         70          0        154        400
```

This says I have 1007MB of RAM

To find out the type of RAM you have:
```

sudo apt-get install dmidecode
sudo dmidecode 
```

There will be a lot of output. Look for a section that looks like this:
```

Memory Device
	Array Handle: 0x0024
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator:  
	Type: **DDR2**
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: CE00000000000000
	Serial Number: 8518F685
	Asset Tag: 020744
	Part Number: M3 78T6553EZS-CE6 

```

---

### Post by Wataru8675 on 2009-08-10
> **Revolutionary101 said:**
> This command should give you all the information you need.

```
sudo dmidecode &#8211;type 6
```

Perfect!  This is exactly what I'm looking for, thanks!

Though a significant correction:  The command is
```
sudo dmidecode -t memory
```If you type "-type6" it tells you that "ype6" is an invalid command, then gives you a list of options.  "Memory", however, is the 6th in the list...correlation, yes, causation...maybe...

Also, unutbu, I'm not sure you have to apt-get install dmidecode.  I ran it straight without installing it and got it to work just fine.  I'm running 9.04, though, so maybe it comes installed automatically on newer versions.

---

### Post by andrew.46 on 2009-08-11
Hi Wataru,

> **Wataru8675 said:**
> Hey all.  I'm looking to install a RAM upgrade into my laptop, even though I probably shouldn't...  I'm in just a little over my head digging around in a computer, but I know the risks and am up for a challenge

You are a braver man than me, I looked at doing the same to my Dell Latitude D520 until I saw that some of the RAM is stored under the keyboard and more than a little difficult to access while the rest of it is a little easier but located underneath the base of the laptop.....

Andrew

---

### Post by Paddy Landau on 2009-08-11
> **Wataru8675 said:**
> Though a significant correction...
Careful. You mistyped it.
```
sudo dmidecode --type 6
```There are two dashes, and a space before the 6.

---

### Post by credobyte on 2009-08-11
> **unutbu said:**
> To find how much RAM you current have, you could open a terminal (Applications>Accessories>Terminal) and type

```
% free -m
             total       used       free     shared    buffers     cached
Mem:          **1007**        937         70          0        154        400
```This says I have 1007MB of RAM

To find out the type of RAM you have:
```

sudo apt-get install dmidecode
sudo dmidecode 
```There will be a lot of output. Look for a section that looks like this:
```

Memory Device
    Array Handle: 0x0024
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator:  
    Type: **DDR2**
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: CE00000000000000
    Serial Number: 8518F685
    Asset Tag: 020744
    Part Number: M3 78T6553EZS-CE6 

```

```
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    **Type: Unknown**
    Type Detail: None
```

:lolflag:

---

### Post by MrWES on 2009-08-11
> **Wataru8675 said:**
> Hey all.  I'm looking to install a RAM upgrade into my laptop, even though I probably shouldn't...  I'm in just a little over my head digging around in a computer, but I know the risks and am up for a challenge.

I couldn't find my RAM cards in my laptop when I was poking around the other day.  Is there a command line prompt that can detect what kind of RAM I'm using (DDR, DDR2, etc.) and how much RAM it has in MB/GB/etc?

I'm hoping that once I get the RAM card I'll be able to find a chip that looks like it in my computer and locate my existing RAM card that way. ^^;

Try NewEgg's memory configuration tool:

[http://www.newegg.com/Store/Category.aspx?Category=17&name=Memory]("http://www.newegg.com/Store/Category.aspx?Category=17&name=Memory")

It's located in the lower left hand corner of that web page. Even if you don't purchase the RAM from them, at least you can ensure which type you need with that tool.

Bill

---

