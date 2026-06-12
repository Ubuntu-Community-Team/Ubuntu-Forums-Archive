---
title: "Issues booting up Ubuntu 10.10 (graphics)"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by MikeTheNewGuy on 2011-03-02
Hi im pretty new to Ubuntu 
I recently built a pc and installed ubuntu 10.10 on it.
When i tried to initially install it every time i got to the install screen the screen would go blank and i would receive an error on my screen saying "input not support"
I did eventually get past this by typing (i cant remember where :O) somethin g along the lines of "xforce vesa"
Well i managed to get it installed but now everytime i boot up i get either the "error imput not supported" message or i only get a terminal type screen.
I can however hold down shift, select recovery mode in the grub menu and select failsafe graphics which looks pretty dumb but does work.

Some specs (copied from terminal)
Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Motherboard
       product: 945GSE
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/17/2010)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot

display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0

So anybody know how i can find a better solution for this?
btw sorry for the wall of text, idk if u can use spoilers here?

---

### Post by slooksterpsv on 2011-03-02
Going off on a limb here, but can you get into Grub, and edit it (before booting) and add the following to the end:

```

nomodeset

```

I keep thinking there 945 drivers... Hmmm, it looks like there may be a PPA to possibly fix this. Here's what you would need to do, and here's the thread I got the information from:

```

sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

```

Thread: [http://ubuntuforums.org/showthread.php?t=1484137&page=2](http://ubuntuforums.org/showthread.php?t=1484137&page=2)

Again I can't verify if this will work, but it's worth a shot.

---

### Post by MikeTheNewGuy on 2011-03-03
Please explain exactly what i must do (what must i edit?)

---

### Post by slooksterpsv on 2011-03-03
Oh I am so sorry, I didn't realize I didn't even explain.

For GRUB, when you boot up your computer, hold down the SHIFT key, you should get a menu like this:

[IMG]http://tipsfromgeek.com/wp-content/uploads/2009/11/GRUB.jpg[/IMG]

Probably the top one will say like: kernel 2.6.35-22

Anyways, press the e key then go down to the line that starts with:

linux / - something like this

[IMG]http://images.maketecheasier.com/2009/12/ubuntukarmic-edit-grub-entr.png[/IMG]

And go to the very end (press the right over key, down arrow won't do it), put a space at the end and type in:

nomodeset

and then press CTRL+X to boot - actually that picture shows where they put nomodeset haha.

Try booting up like that, now for the PPA (which again I can't guarantee if this will fix it or not), if the above doesn't work, do the following - log in, go to Applications -> Accessories -> Terminal.

You should get a black or purple window with something like this:

```

username@name-of-pc:~$

```

Type in the following (pressing ENTER where it says <ENTER>):
```

gksudo add-apt-repository ppa:glasen/intel-driver <ENTER>
gksudo apt-get update && gksudo apt-get upgrade <ENTER>

```

Then after that updates and installs, reboot the computer.

Again I apologize that I didn't explain that too well.

---

### Post by MikeTheNewGuy on 2011-03-04
Ok nomodset doesnt do anything :(
And the second idea didnt work either. when i put the second one in terminal i get a message saying 
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.4MB of archives.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? Y
Then nothing happens now what?

---

