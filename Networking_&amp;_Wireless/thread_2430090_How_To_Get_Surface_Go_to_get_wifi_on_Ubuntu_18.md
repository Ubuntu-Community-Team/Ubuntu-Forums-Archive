---
title: "How To Get Surface Go to get wifi on Ubuntu 18"
date: 2019-10-27
forum: Networking &amp; Wireless
---

### Post by abhishekroy49 on 2019-10-27
Is this the right method to do? :-

[FONT=Verdana]https://www.reddit.com/r/SurfaceLinux/comments/9t53gq/wifi_fixed_on_surface_go_ubuntu_1810/

[LEFT][COLOR=#222222][FONT=verdana]&#8203;
Step 1) Download the board.bin file from here: [http://www.killernetworking.com/support/K1535_Debian/board.bin](http://www.killernetworking.com/support/K1535_Debian/board.bin)  - I saved the file to Downloads -
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step 2) Open the Terminal
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step3) Remove the current board.bin file from directory hw2.1:[/FONT][/COLOR][COLOR=#222222][FONT=verdana]sudo rm /lib/firmware/ath10k/QCA6174/hw2.1/board.bin
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step 4) Copy the board.bin file from Downloads to hw2.1*[/FONT][/COLOR][COLOR=#222222][FONT=verdana]sudo cp ~/Downloads/board.bin /lib/firmware/ath10k/QCA6174/hw2.1
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step 5) Remove the current board.bin file from directory hw3.0[/FONT][/COLOR][COLOR=#222222][FONT=verdana]sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/board.bin
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step 6) Copy the board.bin file from Downloads to hw3.0*[/FONT][/COLOR][COLOR=#222222][FONT=verdana]sudo cp ~/Downloads/board.bin /lib/firmware/ath10k/QCA6174/hw3.0
[/FONT][/COLOR][COLOR=#222222][FONT=verdana]Step 7) Restart[/FONT][/COLOR][COLOR=#222222][FONT=verdana]&#8203;[/FONT][/COLOR][COLOR=#222222][FONT=verdana]
[/FONT][/COLOR][/LEFT]
[/FONT]

---

### Post by chili555 on 2019-10-28
I'm not sure that many of us here have the Surface Go in order to give you the best answer. First, let's see if you have the same wireless device. Please run:

```
lspci -nnk | grep 0280 -A3
dmesg  | grep -e sdio -e ath10k
```My only issue is that I wouldn't remove (rm) the current board.bin unless I knew that the new one worked. Instead, I would back it up and keep it:```
cd /lib/firmware/ath10k/QCA6174/hw2.1/
sudo mv board.bin board.bak


```In that way, you always can restore the old file. If you remove it (rm), it is lost and gone forever.

---

