---
title: "Heat and Temperature OK?"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by AlAK on 2010-08-21
hello,

I am absolutely new to Ubuntu. Have recently installed 10.04 Lucid Lynx. It was running fine until today. Today I kept the computer idle for a while and came back to see that my laptop screen. On restarting it told me that the system was overheated and shut down. 
I let it "cool" down for a while and restarted it and used lm-sensors and hddtemp, here is what I found:

$sensors

temp1:       +71.0°C  (crit = +94.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +67.0°C                                    
Core0 Temp:  +69.0°C                                    
Core1 Temp:  +70.0°C                                    
Core1 Temp:  +70.0°C   

~$ sudo hddtemp /dev/sda
 /dev/sda: ST9160821AS: 46°C


Here is some system information:

uname -a
Linux my-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

processor is AMD Turion (64)  current RAM 2.0 GB (had to remove 1GB RAM card that was malfunctioning) Inspiron 1526.


Questions

1.I understood that my hard disk temperature is 46*C. How to interpret the information given by "$sensors ".?
2.What is generally the comfortable range of temperature for all of the above?
3. I think I have installed 32 bit ubuntu on my 64 bit computer, (though I dont think so)does this cause problem sometimes? Has removing the 1GB Ram (i removed it long ago) the cause of a problem?

Please let me know,

Thanks

---

### Post by earthpigg on 2010-08-21
hi,

AMD processors run hotter than Intel processors in general. Also in general, laptops run hotter than desktops.

> Today I kept the computer idle for a while and came back to see that my laptop screen. On restarting it told me that the system was overheated and shut down. 

was the laptop sitting on anything ***other*** than a hard and flat surface?

alternatively, did you leave anything CPU intensive open when you let it 'idle'? flash is notorious for eating up CPU cycles, for example.

> temp1: +71.0°C (crit = +94.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +67.0°C
Core0 Temp: +69.0°C
Core1 Temp: +70.0°C
Core1 Temp: +70.0°C 

these temperatures aren't anything to be concerned over.

---

### Post by AlAK on 2010-08-22
Hi,

I guess my mistake was leaving it on my bed with lot of firefox tabs open.
But the fact is my laptop is still notoriously heating up, I tried with windows vista and it was still heating up but it didnt shut down.Perhaps the Vista doesnt mind if your system is fried or has a higher critical temperature.When I switched to ubuntu after running Vista for a while, it booted only to shut down immediately. It said its temeperature was then 96*C, (Ubuntu treats 94*C as critical temperature). 

Please let me know what might be wrong? I have lot of important stuff on this so dont want to do it any harm.

---

### Post by earthpigg on 2010-08-22
i'd suggest getting some compressed air, taking the laptop as far apart as you are comfortable doing, and spraying all the dust out. 

you a smoker? smoke around your laptop? if so, you will get a sneak preview of what the inside of your lungs look like. :P

if you are a smoker, and the insides of the computer are covered in tar, you may need to do more than spray it with compressed air.

---

### Post by cespinal on 2010-08-22
> **AlAK said:**
> Hi,

I guess my mistake was leaving it on my bed with lot of firefox tabs open.
But the fact is my laptop is still notoriously heating up, I tried with windows vista and it was still heating up but it didnt shut down.Perhaps the Vista doesnt mind if your system is fried or has a higher critical temperature.When I switched to ubuntu after running Vista for a while, it booted only to shut down immediately. It said its temeperature was then 96*C, (Ubuntu treats 94*C as critical temperature). 

Please let me know what might be wrong? I have lot of important stuff on this so dont want to do it any harm.

Leaving the laptop on the bed is a big no no. 
Also try yo clean it as the previous poster said. 

However, I have to say that since the last kernel updates my gnome desktop was eating all my ram, fan working at full speed and heat being built heavily. Seriously... It was painful to use. 

My solution? switched to xfce. Still using compiz and running a virtual machine with xp, ram never goes above 1.2 gb and I must say I have NEVER felt the pc so cool, with the fan almost being noticeable. 

one just never stops learning...

---

### Post by Norm24 on 2010-08-22
A cooling pad can't hurt either.

---

### Post by techunit on 2010-08-22
The lucid kernel doesn't work well with alot of laptops installing the Karmic Kernel is a documented solution to it running hot, but I am not sure if this is still a problem as It seems to have been fixed with the latest kernel updates. Hope this helps.

---

### Post by earthpigg on 2010-08-22
> **techunit said:**
> The lucid kernel doesn't work well with alot of laptops installing the Karmic Kernel is a documented solution to it running hot, but I am not sure if this is still a problem as It seems to have been fixed with the latest kernel updates. Hope this helps.

based on that information, AlAK, you should ensure your ubuntu is completely up to date.

---

### Post by neilms on 2010-08-22
I invested £20 for a laptop USB cooler. I NEVER use my laptop without it - why? Because I want it to last for many years to come.

---

### Post by AlAK on 2010-08-24
Hello,

@earthpigg @cespinal@neilms @norm24 @techunit
Thanks for all your suggestions. I will try to implement them.

@neilms @Norm24
getting a cooling pad asap.

Meanwhile, I read somewhere on the forum (sorry unable to locate the link) that ATI Radeon graphics card might also be the problem, someone suggested to reinstall the drivers/go for proprietary drivers.

I have reinstalled them for the movement,
$sudo apt-get install fglrx
the computer is heating up (but not as much as before), the only annoying thing is that the fans keep running all the time.

What are the "cool-range" for the computer:What are its usual operating temperatures for a non-overheating computer, any idea? After what temperature do the  fans turn on?

---

### Post by Paqman on 2010-08-24
> **AlAK said:**
> 
I guess my mistake was leaving it on my bed

Beds, sofas, cushions, anything soft like that can block off airflow in and out of the machine, since the vents are on the underneath/sides. That's why they have little feet to create a gap that allows air to flow.

> **AlAK said:**
> Hello,
What are the "cool-range" for the computer:What are its usual operating temperatures for a non-overheating computer, any idea? After what temperature do the  fans turn on?

Depends. Some desktop systems run as cool as 35C, but over 50C is fine for a lot of laptops. Your BIOS is what controls the fans and temperature protection, you should be able to have a look in it to what settings there are. There will be a max temperature in there that it will automatically shut down at to protect itself. The fans normally run all the time in most machines, but their speed is controlled by the load on the machine.

Listen to earthpigg too, if you've had the machine for more than a few months and are in the habit of leaving it sitting on the bed sucking in fluff it might be time for a cleanout.

---

### Post by neilms on 2010-08-24
Im not sure what the prescribed level is before the fans turn on. I now that if i don't use my cool pad, they tend to come on every now and then.

If i were you, i would not keep my laptop on too long, until this problem is fixed.

I think you should think about filing a bug report for your laptop. I dont know a lot about operating system internals, but i would guess that your problem has something to to with ACPI. If you file a bug report and keep checking up on how its going, you will eventually find out what the precise cause is of your fan not working as it should.

---

### Post by pizza-is-good on 2010-08-24
My laptop was running hot a few weeks back, and I mean really hot. It was only giving me problems in Windows when I gamed, ubuntu was fine. I never got an 'emergency shut-down'.

That said, when in windows, the fan would be on constantly and at full speed, with really hot air coming out.

I took it apart and cleaned it. Also had to take the fan apart and clean it. The works part was that the heat sink that is cooled by the fan, which is also the vent through which the air escapes the laptop, had a really thick layer of dirt, which prevented the air from leaving, so the fan was not cooling the heat sink. The fan was also full of dirt.

After cleaning it all out, it works nice and cool now. The fan idles most of the time now, and unless gaming, the air coming out of the vent is either cool or slightly warm.

It had been 2 years since I got the laptop, so I guess it was about time.
Do clean it please, it is the best way to make it faster.
BTW @ earthpigg: Compressed air is not such a good idea in a laptop when you have a lot of dirt in it. If you get dirt/dust in other components, it could worsen things. Try to remove it by hand or q-tips first, then use the air for a final clean up.

---

