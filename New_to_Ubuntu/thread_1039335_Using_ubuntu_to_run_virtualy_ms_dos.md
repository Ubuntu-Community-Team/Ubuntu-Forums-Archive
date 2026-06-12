---
title: "Using ubuntu to run virtualy ms dos"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Medo@Croatia on 2009-01-14
Hi

I have a question

i have POS for my bar and atm no time and money to invest in some newer pos program, so im using the same one for cca. 8 years

i want to play some mp3s and not to have 2 computers id like to know if it is possible to make virtual machine for ms dos and just copy my files from old hard drive on that virtual file and to run it normal while im playing mp3's on ubuntu


in some way the best example would be something like bootcamp in mac os x

---

### Post by Titan8990 on 2009-01-14
You could try dosbox which is a DOS emulator for all platforms. Avaiable in Synaptic.

Although, I don't have a full understanding of what you are trying to do.

---

### Post by Bölvaður on 2009-01-14
> **Titan8990 said:**
> Although, I don't have a full understanding of what you are trying to do.

Indeed.


But as a guess you should look into Virtualbox (installable from Add/Remove and you may need to install correct kernel for virtualbox from System&#8594;Administrator&#8594;Synaptic Package Manager (look for virtualbox and pick same kernel as you have running)).

I dont use virtual machines but I know it is possible to share data or move them between the vm and host.

---

### Post by albinootje on 2009-01-14
> **Medo@Croatia said:**
> 
i want to play some mp3s and not to have 2 computers id like to know if it is possible to make virtual machine for ms dos and just copy my files from old hard drive on that virtual file and to run it normal while im playing mp3's on ubuntu

You can run DOS inside Linux with :

1) Dosbox (already mentioned by someone else)
2) Dosemu
3) VirtualBox
4) Qemu
5) VMware
and probably more.

Dosbox is focused on DOS games, so I bet it's pretty good with sound, but Qemu is also interesting in this case I think.

There are a few GUI based launchers for Qemu :
```

sudo apt-get install qemulator qemu-launcher

```

---

### Post by Paqman on 2009-01-14
I don't quite understand your post either, can you try using less abbreviations?

Do you want to run a DOS program while listening to mp3s in Ubuntu? If so then yes, you should try DOSBox. You don't need a full-blown virtual machine like Virtualbox to run DOS.

---

### Post by Kellemora on 2009-01-14
Hi Medo

I'll save you some headaches here!

You CAN run the software for your POS equipment, BUT you cannot RUN THE DRIVERS REQUIRED to make them work!

That's one of the issues that have kept us from going totally Ubuntu.  No drivers for POS hardware in Linux!

I've even checked with the largest swipe machine data handling company in the world (NOVA) and they too have no support for Linux based readers, even though the machines themselves use Linux internally.  Although they run the entire company on UNIX, so go figure, hi hi.......

There IS an around the horn method using a web browser to access their terminal and tie in the card scanner/reader, but it won't interface with the cash registers that way.

TTUL
Gary

---

