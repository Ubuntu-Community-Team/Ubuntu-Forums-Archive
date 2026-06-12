---
title: "Intel® Killer™ Wi-Fi 6 AX1675 driver is not installed in fresh Ubuntu 20.04"
date: 2024-10-02
forum: Networking &amp; Wireless
---

### Post by stm32h757 on 2024-10-02
Hello,

I have set up a dual-boot system with Ubuntu 20.04 and Windows 11 on my Alienware X15 R2. The wireless LAN card in my laptop is the Intel® Killer&#8482; Wi-Fi 6 AX1675.

According to the [Intel support page]([https://www.intel.com/content/www/us/en/support/articles/000088040/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000088040/wireless.html)), the Linux kernel typically includes the necessary driver for this card. However, it seems that the driver is not functioning correctly on my system. Currently, I can only connect to the internet using a USB-WLAN adapter, as the laptop's wireless card is not working.

I specifically want to use Ubuntu 20.04, as I need it to develop older code for the Jetson TK1.

I did sudo apt-get update and sudo apt-get upgrade successfully.

---

### Post by stm32h757 on 2024-10-02
ubuntu@AlienwareX15r2:~$ lsmod | grep iwlwifi
iwlwifi               446464  0
cfg80211              970752  3 iwlwifi,mac80211,rtl8xxxu

---

### Post by jeremy31 on 2024-10-02
See the wireless script link in my signature and post results

---

### Post by stm32h757 on 2024-10-02
Thank you for your help! I&#8217;m a beginner with Ubuntu.

The results from "sudo apt update" and "sudo apt dist-upgrade" show no issues, and the system is up to date:
- [Terminal screenshot for "sudo apt update"]([https://drive.google.com/file/d/1HgHrqsyAhL1BhOSa_C19gxhXMLt9CBZ9/view?usp=drive_link](https://drive.google.com/file/d/1HgHrqsyAhL1BhOSa_C19gxhXMLt9CBZ9/view?usp=drive_link))
- [Terminal screenshot for "sudo apt dist-upgrade"]([https://drive.google.com/file/d/1RL4AloUn6zu4XUXNHCcT58ReBKo4wVt4/view?usp=drive_link](https://drive.google.com/file/d/1RL4AloUn6zu4XUXNHCcT58ReBKo4wVt4/view?usp=drive_link))

Here are the results from the wireless-info script:
- [Wireless Info (txt file)]([https://drive.google.com/file/d/1trbdv1rPIGNykAEVLLzFaV2pjqIRmx_Q/view?usp=drive_link](https://drive.google.com/file/d/1trbdv1rPIGNykAEVLLzFaV2pjqIRmx_Q/view?usp=drive_link))
- [Wireless Info (tar file)]([https://drive.google.com/file/d/195R_2qeMTZZyOpr9DHkyS0QLp9lAJa-K/view?usp=drive_link](https://drive.google.com/file/d/195R_2qeMTZZyOpr9DHkyS0QLp9lAJa-K/view?usp=drive_link))

---

### Post by stm32h757 on 2024-10-02
I disabled "fast-boot" on windows but didn't work.

---

### Post by him610 on 2024-10-02
> The wireless LAN card in my laptop is the Intel® Killer™ Wi-Fi 6 AX1675....I specifically want to use Ubuntu 20.04.
I don't know for sure, but it could be that LTS 20.04 did not have driver for that particular wifi 6 card. It may be necessary to go with more recent release.

---

### Post by stm32h757 on 2024-10-02
I tried Ubuntu 22.04, and the live filesystem on USB was able to detect my wireless LAN card without additional setup. I'll proceed with using Ubuntu 22.04. Thank you.

---

### Post by stm32h757 on 2024-10-04
Installing Ubuntu 22.04 worked for me, but I&#8217;m curious if there&#8217;s anything to be discovered from the results of my wireless script for future users. I&#8217;m also considering reinstalling Ubuntu 20.04 if I can get the wireless driver to work.

---

