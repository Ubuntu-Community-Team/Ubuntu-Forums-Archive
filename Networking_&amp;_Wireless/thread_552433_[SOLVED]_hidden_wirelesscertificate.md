---
title: "[SOLVED] hidden wireless/certificate"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by teh'p3nsi0n3r on 2007-09-16
ok so i am going back to university tommorow and would like to be able to use the wireless my university provides throughout their building.
I have used it previously 6 months ago on an old laptop using windows xp and an intel pro wireless card, to do this using windows i had to 1st get authorisation from the university to use there network by supplying them with my netword cards mac address (shouldnt be an issue) next came the part of setting up the laptop/wiress to find there "hidden" wireless signal, this is where i am unsure, using windows i had to download a certificate from the university portal, my questions are, can i use this certifcate with (K)ubuntus network manager? how can i use there wireless if not?, supplying instructions of there setup is not an issue ill just login and supply the windows setup info if it will help. i have been using ubuntu for the past 7 months and have been happy since using (K)ubuntus network manager to connect to my home wireless. (picks up the wireless signal no problem as isnt hidden).
I am sure there are similar threads about hidden wireles networks but i am unsure if they are they are the same methods my university is using, i am not sure about wireless network methods etc.
i really dont want to have to go back to windows on my laptop if i dont have to ;) rubbish.

---

### Post by teh'p3nsi0n3r on 2007-09-16
i thought this information might help.

wireless setup guide from universitys website that was in (pdf) format.
its on a secure server so ive uploaded the pdf to a filehosting site.

[http://files-upload.com/files/506602/AbertayCONNECT%20Wireless%20Setup%20for%20Windows%20XP.pdf]("http://files-upload.com/files/506602/AbertayCONNECT%20Wireless%20Setup%20for%20Windows%20XP.pdf")



> Install WiFi Certificates

AbertayCONNECT Wireless Service (WiFi) Security Certificates

The  UAD Enterprise Root CA and WirefreeUAD digital certificates can be downloaded by clicking on the following link: - Airconnect.pb7  Click to download WiFi certificates  new

Choose Save in the File Download dialogue box.

[IMG]https://portal.abertay.ac.uk/portal/page/portal/Helpdesk/images/WorkingontheMove/WiFi/Certificates/FileDownload.JPG[/IMG]


Save the certificate installation file to a removable storage device (or directly to your laptop if you are doing this at home), then carry out the steps detailed below.

 [IMG]https://portal.abertay.ac.uk/portal/page/portal/Helpdesk/images/WorkingontheMove/WiFi/Certificates/SavetoUSB.jpg[/IMG]

Installing the certificates

The following steps must be carried out on your laptop:

   1. Locate the Security Certificate installation file 'Airconnect.p7b' that you saved earlier. Right click on this file, and in the context menu that appears choose 'Install Certificate'.[IMG]https://portal.abertay.ac.uk/portal/page/portal/Helpdesk/images/WorkingontheMove/WiFi/Certificates/Installcer.jpg[/IMG]

   2. The Certificate Import Wizard will now be displayed:

          * Click Next to continue
          * In the Certificate Store window that appears just keep the default option to 'Automatically select the certificate store'. Click Next again.
          * In the Completing the Certificate Import Wizard window click Finish.

   3. The following Security Warning dialogue will now be displayed. Click Yes to install the certificate.

       [IMG]https://portal.abertay.ac.uk/portal/page/portal/Helpdesk/images/WorkingontheMove/WiFi/Certificates/CertSecurityWarning.JPG[/IMG]

      You should now refer to the guide How to configure your laptop for AIRCONNECT (WLAN) to complete the remaining steps for connecting to the wireless network.

---

### Post by teh'p3nsi0n3r on 2007-09-16
bump

---

### Post by jjmatt on 2007-09-18
You should be able to enter the network manually in the network manager applet. Just get the essid (network name) and password if necessary

However, I have been having problems connecting to my hidden wireless network at home. I tried this, but then it never connected...

Let me know if you figured out how to do it.

---

### Post by teh'p3nsi0n3r on 2007-09-20
hi thanks for the response, ive had submitted my mac address to my university and theyve granted me access of course they only officially support windows/mac, i still cant get connected, the wireless signal is showing "airconnectuad" and "airconnect" in knetwork manager and when i select one of them ive tried making the setting similar to the ones in the universitys pdf instructions, there is one for mac and one for windows, i have also downloaded the certficate and selected that also.

The settings i have used were "WPA Enterprise" 

identity: my student id e.g. 0145674 (is same amount of digits)

and the password for my student account.

specified a certficate i downloaded from there site, and i have done these steps both for airconnectuad and airconnect but still nothing, any help?

---

### Post by teh'p3nsi0n3r on 2007-09-20
> **teh'p3nsi0n3r said:**
> hi thanks for the response, ive had submitted my mac address to my university and theyve granted me access of course they only officially support windows/mac, i still cant get connected, the wireless signal is showing "airconnectuad" and "airconnect" in knetwork manager and when i select one of them ive tried making the setting similar to the ones in the universitys pdf instructions, there is one for mac and one for windows, i have also downloaded the certficate and selected that also.

The settings i have used were "WPA Enterprise" 

identity: my student id e.g. 0145674 (is same amount of digits)

and the password for my student account.

specified a certficate i downloaded from there site, and i have done these steps both for airconnectuad and airconnect but still nothing, any help?

Also the above instructions as mentioned before are from the universitys portal, the pdf instructions i posted have their setup info.

---

### Post by teh'p3nsi0n3r on 2007-09-20
anyone? :(

---

### Post by teh'p3nsi0n3r on 2007-09-20
> **teh'p3nsi0n3r said:**
> anyone? :(

?

---

### Post by quill7111 on 2008-01-28
I suppose this thread is dead, but I'd be really curious to see if anyone has a solution.

---

### Post by teh'p3nsi0n3r on 2008-02-05
sorry i forgot about this thread, actually i am now using the network manager using nm-applet for detecting wireless.

latest version of gutsy 7.10 fixed this issue for me :) wireless network is hidden so "connect to other wireless network" 

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

apply the apropriate settings from the options, like PEAP / TKIP, mschapv2 etc....

i got a converted windows certificate converted to .pem file from the abertay lug which is the certificate i imported.

[http://www.thelinuxsociety.org.uk/howto2.html](http://www.thelinuxsociety.org.uk/howto2.html)

i did not use wpa supplicant though the terminal like on that guide just the certificate.
Been happily connected since latest release of ubuntu, hope this helps :)

---

