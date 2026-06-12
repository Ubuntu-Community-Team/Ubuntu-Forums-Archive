---
title: "Network Lost"
date: 2020-10-25
forum: Networking &amp; Wireless
---

### Post by asearle on 2020-10-25
Hallo Everyone,

I have got myself into a very silly situation ...

On a laptop that I am setting up (HP ProBook 4540s), I couldn't get Bluetooth to work. So I decided to first remove and then re-install.

But somehow my removal of the Bluetooth components also removed my network support.  Arrrggghhh!

So I have two questions ...

1. Which package(s) do I need to re-install?
2. How do I get these packages from the install medium (a USB stick): Without network access, I cannot get the packages from the network.

Any tips for me?  Or a link to a HOWTO?

Many thanks,
Alan

---

### Post by yapidumoac on 2020-10-27
'How to reinstall network manager without internet access?'

[https://askubuntu.com/questions/422928/how-to-reinstall-network-manager-without-internet-access](https://askubuntu.com/questions/422928/how-to-reinstall-network-manager-without-internet-access)

---

### Post by asearle on 2020-10-28
Hallo Everyone,

yapidumoac:  Many thanks for the link.

I trawled through a number of solutions with some looking extremely complicated.

Then I happened upon what I thought was the ideal solution:  To burn and install DVD and in Muon or Discover adjust the Software source to include the install DVD.  That looked ideal.

But even though there was an option to "Add CD" to the software libraries, the system wasn't able to detect the DVD.

I then looked on the install DVD for ".deb" files (to copy across) but couldn't find any.

Can anyone help me here?  Can I declare the install DVD as a software source in a setup-file or at the command line?

Many thanks for any tips.

Yours,
Alan

---

### Post by yapidumoac on 2020-10-28
Try this ..

"how do I install a network manager on Ubuntu?"

[https://askubuntu.com/questions/319798/how-do-i-install-a-network-manager-on-ubuntu](https://askubuntu.com/questions/319798/how-do-i-install-a-network-manager-on-ubuntu)

Else try this ..

Don't forget to save your /home directory to external media before trying this. Boot from the DVD, select the "installation type" screen, then choose 'something else', select the (old) root partition "/" and deselect the "format" checkbox. (**important**). And click on 'install'. This will replace the missing files and leave the others. Select the same username and password as the old system. Reboot into safe mode and then copy back the contents of your external /home directory.

---

### Post by asearle on 2020-10-28
MANY THANKS!

yapidumoac's tip got it fixed  :-)

---

