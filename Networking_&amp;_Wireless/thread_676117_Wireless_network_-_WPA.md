---
title: "Wireless network - WPA"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by b1g4L on 2008-01-23
Yes I know there are a million threads on this, but I cannot get this figured out. I am running Ubuntu 7.10 on a Dell D620 with Intel wireless chipset. I am able to connect to my router at home which uses WEP and I can connect to other open networks fine using network manager. The trouble I am having is connecting at school. Here is a description of the network taken from the steps to setup the connection in XP:

SSID: CWPPA

Network Authentication: WPA

Data Encryption: TKIP

Enable IEEE 802.1x authentication 

EAP Type: PEAP

Do NOT Validate server certificate


I have tried editing the interface file and messed with wpa_supplicant, but have failed to connect. I tried wpa_gui which would seem to simplify the configuration of wpa_supplicant - it gives a message "Failed to open control connection to wpa_supplicant".

One thing I should note is that I do not get the wireless strength signal icon in my sys tray. I have seen others able to right click and go to connect to other wireless networks and such, but I only have the network monitor icon.

Any help would be greatly appreciated. Thanks,

---

### Post by JK21 on 2008-01-23
Try this:

Procedure to enable WPA Wireless in Ubuntu

To update the source list run the following command:
sudo apt-get

Then:
sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces
Comment out everything other than &#8220;lo&#8221; entries in that file and save the file

sudo gedit /etc/default/wpasupplicant
Add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command
sudo /etc/init.d/dbus restart

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new &#8220;keyring&#8221;.

Hope this works (it did for me !)

Grtz Jo

---

### Post by b1g4L on 2008-01-23
Awesome. This worked perfectly. Thanks so much!

---

### Post by JK21 on 2008-01-24
> **b1g4L said:**
> Awesome. This worked perfectly. Thanks so much!

Glad I could be of help :)

---

### Post by wieman01 on 2008-01-24
> **JK21 said:**
> sudo gedit /etc/default/wpasupplicant
Add entry ENABLED=0 and save the file

Grtz Jo
Out of curiosity... What does adding that entry do? Why would one have to do it?

Another thing... wpa-supplicant is installed by default (Gutsy). So why would we reinstall it?

I am trying to understand the steps you have outlined, that's all. :-)

---

### Post by b1g4L on 2008-01-24
I believe he was just making sure I had it installed, which I did - so I just skipped that step. Not sure what the ENABLED = 0 does to WPA_Supplicant.

---

### Post by JK21 on 2008-01-24
> **wieman01 said:**
> Out of curiosity... What does adding that entry do? Why would one have to do it?

Another thing... wpa-supplicant is installed by default (Gutsy). So why would we reinstall it?

I am trying to understand the steps you have outlined, that's all. :-)

You're right about the enalbed-thing. It's not needed in Gutsy if everything goes OK when installing WLan. But back to Feisty or Dapper (can't remember to be honest) I had this little problem and found this workaround to get everthing at work properly. Since the 'comment out' didn't do the trick then...

About your 2nd question:
I found out that reinstalling wpa-supplicant is sometimes a better option instead of trying to get it 'alive' again. That's why :)

---

### Post by wieman01 on 2008-01-24
> **JK21 said:**
> You're right about the enalbed-thing. It's not needed in Gutsy if everything goes OK when installing WLan. But back to Feisty or Dapper (can't remember to be honest) I had this little problem and found this workaround to get everthing at work properly. Since the 'comment out' didn't do the trick then...

About your 2nd question:
I found out that reinstalling wpa-supplicant is sometimes a better option instead of trying to get it 'alive' again. That's why :)
OK, makes sense then. First time I have seen such thing, therefore I thought I'd better ask. Thanks.

---

