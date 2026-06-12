---
title: "Wireless problem (ubuntu 8.04)"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Nabeel Ali on 2008-08-06
Hi,
wireless connection was  not working so I past those commands in the terminal 
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl394    col
after that wireless starts working and I browsed internet and there was no problem but after restarting my laptop I couldn't brows internet whoever wireless is working and I can get good signal

---

### Post by pytheas22 on 2008-08-06
It looks like you may have had a typo in your last command.  The correct command should be:
```

echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Try that.  If it still doesn't work upon reboot, there are other ways to fix it, so please let us know.

---

### Post by Nabeel Ali on 2008-08-07
I got (Permission denied)
any suggestion?

---

### Post by pytheas22 on 2008-08-07
That command needs to be run as root, so use sudo:

```
sudo echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Sorry, I should have mentioned that yesterday.

---

### Post by Nabeel Ali on 2008-08-07
Same problem (bash: /etc/modprobe.d/iwl3945: Permission denied)

---

### Post by pytheas22 on 2008-08-08
Alright, run this:
```

sudo -s
cd /etc/modprobe.d/
chmod +w iwl3945
chmod +x iwl3945
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > iwl3945
```

If that doesn't work, please post the output of:

```
cat /etc/modprobe.d/iwl3945
ls -al cat /etc/modprobe.d/iwl3945
```

---

### Post by Ayuthia on 2008-08-08
> **pytheas22 said:**
> That command needs to be run as root, so use sudo:

```
sudo echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Sorry, I should have mentioned that yesterday.
Usually the > command does not work with a protected file because it does sudo the first half before the > but can't for the second half.  Another way of doing this is:
```
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' | sudo tee -a /etc/modprobe.d/iwl3945
```

---

### Post by Nabeel Ali on 2008-08-08
here is the command and output

nabeel@nabeel-laptop:~$ cat /etc/modprobe.d/iwl3945
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
nabeel@nabeel-laptop:~$ ls -al cat /etc/modprobe.d/iwl3945
ls: cannot access cat: No such file or directory
-rwxr-xr-x 1 root root 55 2008-08-09 00:48 /etc/modprobe.d/iwl3945
nabeel@nabeel-laptop:~$

---

### Post by pytheas22 on 2008-08-08
Alright, it looks like things should be the way they should now.  If you reboot do you still have issues with wireless?

---

