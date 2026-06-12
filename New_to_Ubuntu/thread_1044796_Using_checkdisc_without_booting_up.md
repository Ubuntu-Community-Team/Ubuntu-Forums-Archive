---
title: "Using checkdisc without booting up?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Pascal11110 on 2009-01-19
My sisters computer will not boot up, it just shows a black screen after it does the bios. I have had to reload it 5 times now (first time it just slowed down to incredibly slow and froze all the time, second time did the same, third time got antivirus pro 2009, fourth time was getting slow again, fifth time just loaded it with my MSDN copy of xp so I din't have to use the toshiba crap it came with), so I am thinking that maybe the hard drive is going bad, so I want to use check disc and run some diagnostics on the computer but with a live cd. Know any good ones that I can figure out how to use on the go?

---

### Post by cmnorton on 2009-01-19
You need a recovery disk like Knoppix or the live CD of Ubuntu. checkdisk is part of Windows, so you would need a Windows recovery CD. A Linux recovery disk would at least let you see if the hard drive could be mounted 

It's not clear from your post what is installed on this computer.

---

### Post by Pascal11110 on 2009-01-19
Windows XP Pro is installed on the computer. If I use a live Ubuntu CD, are there any hard drive fitness tests in that?

---

### Post by mrbiggbrain on 2009-01-19
> **Pascal11110 said:**
> Windows XP Pro is installed on the computer. If I use a live Ubuntu CD, are there any hard drive fitness tests in that?

I doubt there would be for NTFS which is what you should use for HDD with XP. It wont matther what version your useing, you just need to get ahold of an OEM or Retail copy of windows xp home/pro.

worst case, there is a vista recovery disk w/o installer that might work, fot sure if it accepts XP, but chkdsk might work even on XP.

---

### Post by Pascal11110 on 2009-01-19
so just run a repair with the XP disc and then do some drive fitness tests after that?

---

### Post by Pascal11110 on 2009-01-19
Solved the problem. I just used the XP install disc to run the recovery console, and used chkdsk in that. It found at least one error, and I am repairing the windows install right now.

---

