---
title: "Accessing wireless from VM VirtualBox"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Jalexa5834 on 2011-04-24
First, thanks for any help you may offer!

I have a Compaq/HP 6715b laptop and I'm using ubuntu 10.10 for my OS. REALLY like the stability over same PC when using XP!

I have loaded VM VirtualBox and with the exception of my wireless connection, it's running great! This virtual XP is faster and more stable that when it was the native OS! I've searched all over the forums and can't seem to either find or understand the answer to my issue. 

My laptop has both wireless and wired connections. (I use one or the other, depending on my location.) For my normal "ubuntu" sessions, I'm able to use either connection, as needed, to access the internet. From within the VirtualBox "XP" session, the laptop isn't "seeing" the wireless connection. The wired connection works great.

Can someone point me in the right direction, please?

Thanks!

---

### Post by rosencrantz on 2011-04-24
A vague wave in the general direction - what does it say (go Advanced...) in the Network Settings dialog for your virtual machine? (hyperlink on the lower right side of the main window)
And what's your VBox version? I recently had to downgrade from 4.0.x to 3.2 because I didn't get USB to work. Use the one from the VirtualBox homepage, and not the Ubuntu repos one.
If it's a recent version (>4.0), you might need an extension pack, also available from the homepage.

---

### Post by lmarmisa on 2011-04-24
Welcome to the forums.

Are you using Bridged Adapter mode for you XP virtual machine?.

If so, you will probably have two interfaces for the adapter (look at Name): a first one for wired and a second one for wireless connections. Select the most appropriate according your needs.

Best regards,

Luis

---

### Post by lmarmisa on 2011-04-24
This capture of the network settings of a virtual machine belongs to a laptop running Ubuntu. You can see here the two interfaces eth2 and wlan0.

---

