---
title: "Installed Ubuntu, now can't boot into windows"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Ulttima on 2009-02-08
I recently installed Ubuntu on an ext drive to try it for the first time.  The grub menu will come up and shows both Ubuntu (along with the recovery mode and memtest options) and Vista.  It will boot into Ubuntu just fine but when I choose Vista I get:

Error 29: Disk write error
Press any key to continue...

doing so takes me back to the grub menu.  If anyone has any ideas on how I can boot into windows that would be great.

---

### Post by tehforum on 2009-02-08
I'm not sure, but the way I do is when the BIOS black background and white text things come up, press Esc, and try from there using the arrow keys to go up or down, and use enter to select.

---

### Post by Ulttima on 2009-02-08
The esc button has no effect from that menu for me.  I am able to select the windows option from the menu but it gives me the error as I described above.

---

### Post by halitech on 2009-02-08
from the archives, hope it helps

[http://ubuntuforums.org/archive/index.php/t-417908.html](http://ubuntuforums.org/archive/index.php/t-417908.html)

check out the post by audiobahn

---

### Post by Ulttima on 2009-02-08
I'll try some things mentioned in that post and let you know how it goes.

---

### Post by caljohnsmith on 2009-02-08
Ulttima, if you have a "savedefault" line in your Vista entry in Grub's /boot/grub/menu.lst file, how about removing that and let me know if you still get the error 29. If you do, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Ulttima on 2009-02-08
Got Vista to boot.  I commented out the savedefault line in the menu.lst file.  Something similar was mentioned in the post linked by Halitech.  Thanks for your help everyone and I look forward to trying out Ubuntu now.

---

