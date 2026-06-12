---
title: "Hard Drive Spinning"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by JumpForJoy on 2009-12-01
Hey,
The hard drive on my Ubuntu server doesn't stop spinning. I as long as its on, my computer makes this horridness sound. To me, it sounds like my hard drive spinning, but it could also be the fan (it's an old computer). Is there any commands I can use, to test wether or not my hard drive is spinning? or what my computer's internal temperature is (or at least if the fan is spinning, because I doubt my computer has a thermostat inside)? And if it is my hard drive spinning, is there any way I can force it to spin down after a certain time on inactivity? Any help/advice would be greatly appreciated.

Also, I have mounted another hard drive to my computer, which is the one that I suspect is spinning non-stop. There is a great chance that I mounted it wrong, but I can't remember how I mounted it. I don't often read/write to this hard drive, so it puzzles me why it doesn't stop spinning.

I just ran "sudo hdparm -S 2 /dev/sdb" and "sudo hdparm -S 2 /dev/sda", but only sdb idles, sda keeps spenning (according to sudo hdparm -C /dev/sda)

Thanks,
Jump For Joy

Also, I decided to copy my topic to the "Absolute Beginner Talk", because I don't know a lot about ubuntu.

---

### Post by Paqman on 2009-12-01
If it's your hard drive that's making a lot of noise, then you're in big trouble. That drive will fail soon.

It's much more likely to be a fan. Open the case and see if you can figure out which fan it is (CPU, PSU, case, GPU, etc). Watch out for cables and such fouling the fans, too.

---

### Post by JumpForJoy on 2009-12-01
Alright, thanks.  Is there any commands I can use to find out if its the fan or hard drive? Or should I just open it up?

Thanks,
JumpForJoy

---

### Post by Paqman on 2009-12-01
Opening it up and having a look and a listen is by far the easiest thing you could do.

Your machine _does_ have temperature sensors inside, btw. It also knows how fast your fans and hard drives are spinning, and lots of other stuff. But since your problem is hardware then software tools are only going to tell you about symptoms, not causes.

---

### Post by 73ckn797 on 2009-12-01
Sometimes you have to open the hood and look for the source of the problem.

---

### Post by Some Penguin on 2009-12-01
> **JumpForJoy said:**
> Hey,
The hard drive on my Ubuntu server doesn't stop spinning. I as long as its on, my computer makes this horridness sound. To me, it sounds like my hard drive spinning, but it could also be the fan (it's an old computer). Is there any commands I can use, to test wether or not my hard drive is spinning? or what my computer's internal temperature is (or at least if the fan is spinning, because I doubt my computer has a thermostat inside)? And if it is my hard drive spinning, is there any way I can force it to spin down after a certain time on inactivity? Any help/advice would be greatly appreciated.

Re: temperature, 
check /proc/acpi/thermal_zone/*/temperature

The fan may become noisier if it or the bearing has developed problems -- an unbalanced fan may be much noisier than normal and should produce an oscillating hum.  The vents may also be less efficient and ventilation if they're dusty -- which you might be able to deal with using a small hand vacuum.  Be careful if you use compressed air dusters, since they may leave a residue.

If the hard drive is continuously spinning, perhaps something is continually reading or writing different data so the cache isn't helping much.  You might want to check 'top' and see what's running.  Maybe something is failing and continuously writing to a log, maybe some indexing service is being run.    Hard to say what without looking at the process list and exploring in detail based on that.

---

