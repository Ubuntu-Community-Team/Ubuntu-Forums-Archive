---
title: "Toshiba Wireless driver help"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by trdconsult on 2008-09-17
Has anyone else noticed this?  I see all these instructions as to how to get the wireless card in the Toshiba laptops to work.  The ironic part is that they all tell you to DOWNLOAD a file from the internet.  

I have the madwifi file downloaded from my Vista partition (madwifi-hal-0.10.5.6-r3835-20080801.tar.gz) and now sitting on a jump drive.  The problem is that I don't know how to install it into Ubuntu from there.  What do I need to do next?

---

### Post by rlzyoner on 2008-09-17
You need to extract the file
tar -xvzf EXTRACTED_FILE
hop into the directory of the extracted file
cd EXTRACTED_FILE
./configure
make 
make install

---

### Post by trdconsult on 2008-09-17
Sorry, I should have been more specific about my abilities.  The last time I had a computer where I was likely to use a command line was my brand new Commodore 128.  Can you make those instructions more specific - I'm not really sure what you mean by "hop".  :)

---

