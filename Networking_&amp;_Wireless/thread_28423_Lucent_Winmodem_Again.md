---
title: "Lucent Winmodem Again"
date: 2005-04-20
forum: Networking &amp; Wireless
---

### Post by salmankhilji on 2005-04-20
I have a Lucent Winmodem on a Compaq Presario 6250us.  I am experiencing problems connecting to the internet using the Hoary LiveCD.

First of all, the system does not auto-detect the modem.  I have to do the following to create /dev/ttLTM0:

sudo modprobe lt_serial
sudo modprobe lt_modem

Then I did:

System -> Administration -> Networking.  Selected "Modem connection" and clicked Properties.  Then I clicked "This device is configured" checkbox and entered the phone number.  From the Modem tab, I entered /dev/ttLTM0 in the modem port.  Autodetect does not work.  After saving the connection, I clicked the "Activate" button.  Even though I had selected "Loud" volume, I did not hear anything from the modem.  It was quiet and did not connect.  The GUI after a few seconds says that the Modem is active, but there is no valid internet connection.

After this I tried 'sudo pppconfig' and after entering the isp info, I tried 'sudo pon paknet', where paknet is the name of the isp.  This time the modem was also quiet and did not respond.

What am I missing?

ubuntu@ubuntu:/etc/ppp/peers$ lsmod | grep -i lt
lt_serial              17888  3
lt_modem              567536  3 lt_serial
cfbimgblt               3072  2 vga16fb,vesafb

ubuntu@ubuntu:/etc/ppp/peers$ ls -l /dev/modem
lrwxrwxrwx  1 root root 11 2005-04-20 13:47 /dev/modem -> /dev/ttLTM0

---

### Post by Turin Turambar on 2005-04-20
I just didn't have any luck configuring my modem with the built-in drivers that came with Ubuntu! I have managed my modem to work, but it didn't want to connect due to some irq errors.
There are, however, free drivers called "ltmodem-2.6-alk-7.tar.bz2" that just work!
They helped me in SuSE and now in Ubuntu.

You have to compile them yourself - just follow the readme file. After you finished everything, just add the driver called "ltserial" (NOT lt_serial!) to the /etc/modules list.

Good luck!

---

### Post by Nob on 2005-04-21
[QUOTE=Turin Turambar]I just didn't have any luck configuring my modem with the built-in drivers that came with Ubuntu! I have managed my modem to work, but it didn't want to connect due to some irq errors.
There are, however, free drivers called "ltmodem-2.6-alk-7.tar.bz2" that just work!
They helped me in SuSE and now in Ubuntu.

You have to compile them yourself - just follow the readme file. After you finished everything, just add the driver called "ltserial" (NOT lt_serial!) to the /etc/modules list.

Good luck![/QUOTE]
 yea, thats the only way... worked with all distros before..
but how can i compile driver when there isnt kernel-source in /usr/src ?

in readme file, it says that we must edit makefile and set correct KERNEL_DIR path to kernel source. but there isnt source for kernel in ubuntu...

what did you do?

---

### Post by Turin Turambar on 2005-04-21
[QUOTE=Nob]yea, thats the only way... worked with all distros before..
but how can i compile driver when there isnt kernel-source in /usr/src ?

in readme file, it says that we must edit makefile and set correct KERNEL_DIR path to kernel source. but there isnt source for kernel in ubuntu...

what did you do?[/QUOTE]

Although ubuntu CD does not contain kernel source, it does have a kernel headers - that's enough for the drivers to compile.
So, just install kernel headers with Synaptic or apt-get. Then follow the instructions.
It's also very important to make a /dev/ttyLTM0 -> /dev/modem symlink.
And it really isn't that complicated. :)

---

### Post by az on 2005-04-21
The package is linux-headers and you also need build-essential

---

### Post by Turin Turambar on 2005-04-21
I successfully compiled the drivers without build-essential. :)

---

