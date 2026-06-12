---
title: "trouble with passwords"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Zundap on 2011-04-03
Hi, could anyone please tell me. if it is possible to use ubuntu live cd to access my windows computer, to by pass the password on hard drive and in the bios. I can use the computer, thats not a problem, but i want to install ubuntu on it instead of windows.


The computer i bought for granddaughter, is now mine as she has a laptop, but Dixon who i bought the computer from, wont give me the password, they say will do it for me, but want to charge me for it,

This to me seems like extortion, they never told us it was password locked when we bought the computer otherwise i would not have bought. i would sooner scrap the computer than give way to their demands, so i would like to know if the live cd could be used to remove the passwords, its either that or scrap it. 

Thanks.

---

### Post by matt_symes on 2011-04-03
Hi

> **Zundap said:**
> Hi, could anyone please tell me. if it is possible to use ubuntu live cd to access my windows computer, to by pass the password on hard drive and in the bios. I can use the computer, thats not a problem, but i want to install ubuntu on it instead of windows.


The computer i bought for granddaughter, is now mine as she has a laptop, but Dixon who i bought the computer from, wont give me the password, they say will do it for me, but want to charge me for it,

This to me seems like extortion, they never told us it was password locked when we bought the computer otherwise i would not have bought. i would sooner scrap the computer than give way to their demands, so i would like to know if the live cd could be used to remove the passwords, its either that or scrap it. 

Thanks.

Ubuntu could bypass the password on windows to get to the file system but not the one on the BIOS. 

It could not be used to run windows though. It could just b used to get files or to install Ubuntu on the drive. 

Is the windows filing system encrypted ?

Out of interest, what is the make of the computer. Depending on the make/model resetting the CMOS might remove the BIOS password.

Kind regards

---

### Post by Zundap on 2011-04-03
Thanks matt, thats all i need, i just want to install ubuntu, is their an instruction tutorial that would show me how i would do that?

---

### Post by matt_symes on 2011-04-03
Hi

The first thing you will need to do is remove the BIOS password by resetting the CMOS. That will be detailed in your motherboard manual using jumpers or you could just take the CMOS battery out for 5 minutes. 

That is _not_ guaranteed to work and could brick the PC.  It depends on the make and model of your PC. However, as you are thinking of binning it if you cant fix it then give it a go if you want.

You never did mention your PC make/model.

You would then need to change BIOS boot order to boot from CD first. You enter the BIOS by pressing a key at the very start of the boot process. It's usually esc, del or a function key.

Pop the Ubuntu CD in the drive, power up and install as usual.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You might be lucky and the CD might be the first boot device anyway.

Kind regards

---

### Post by Zundap on 2011-04-03
The model is Acer Aspire T180 0A72, Would the live cd allow me toe enter the BIOS, to allow me to set the boot order?

---

### Post by matt_symes on 2011-04-03
Hi

> Would the live cd allow me toe enter the BIOS, to allow me to set the boot order?

I think you misunderstand me. 

The live CD is not used to enter the BIOS or reset the BIOS password. 

To remove the BIOS password you need to reset the CMOS using either jumpers on the motherboard or by removing the CMOS battery. 

Once the BIOS password has been reset you can then change the device boot order in the BIOS. 

That allows you to put the CDRom (or other device) as the first bootable device.

This is required only if the hard drive is the first bootable device as you will not be able to boot into the CDRom to install Ubuntu until the CDRom is set as the first bootable device.

You would then install Ubuntu as normal.

As i said, it could brick the PC. I don't know enough about that make or model.

Kind regards

---

### Post by idoitprone on 2011-04-03
you can always call the manufacturer? they might have a backdoor password or some simple method?

---

### Post by Zundap on 2011-04-03
Thanks matt, now i understand what you mean, i will give that a go first thing to morrow, thanks again fior your help.

Thanks idoitprone, while i have the feeling that, they will just refer me back to the company i bought it from, it is still worth a try. Thanks, i will try that first, them matts idea if that fails and if it ends up in the bin, then so be it, but sooner that than give way to legalized extortion.

If if anyone out there is thinking of buying a computer from dixons, bear this sad tale in mind.

Thanks again to you both.

---

### Post by matt_symes on 2011-04-03
Hi

Good luck :D. Tell us how it goes.

Kind regards

---

### Post by grahammechanical on 2011-04-03
On my motherboard there are three pins with CLRTC printed underneath. Two of the pins are linked together or jumped across. CLTRC - Clear Real time Clock and this is what my motherboard manual says:

> This jumper allows you to clear the Real Time Clock (RTC) RAM in CMOS. You can clear the CMOS memory of date, time, and system setup parameters by erasing the CMOS RTC RAM data. The onboard button cell battery powers the RAM data in CMOS, which includes system setup information such as system passwords.

These are the steps:

> 1) turn off the computer and remove the power cord. 2) remove the onboard battery. 3) move the jumper cap from pins 1-2 (default). Keep the cap on pins 2-3 for about 5 - 10 seconds, then move the cap to pins 1-2. 4) reinstall the battery. 5) plug the power cord and turn on the computer. 6) hold down the <del> key during the boot process and enter BIOS setup to re-enter data.

Hope this make things a bit clearer.

Regards.

---

### Post by matt_symes on 2011-04-03
Hi

@grahammechanical That was good clarification.

I was just thinking that most new BIOS's has a quick choose boot key. If yours is new enough and has this option you may not need to clear your BIOS to install Ubuntu. On my laptop it's F12.

If not the method will be something similar to what grahammechanical has just outlined and will be detailed in your motherboard manual. You can download the manual from the manufacturers web site. 

Kind regards

---

### Post by Zundap on 2011-05-17
Sorry about the late reply, i have had health problems, i took the battery out and left it out for a day, then rebooted it, and now the password is no longer needed. That applies to entering the BIOS as well as the boot order. Thanks to you guys i can now install UBUNTU on to it, thanks everyone for your help. :)

---

