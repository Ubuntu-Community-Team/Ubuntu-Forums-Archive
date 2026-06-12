---
title: "Network manager disappeared"
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by podobin on 2021-01-24
hello,

experienced noob here

some time ago i started to have my wifi disconnected (later on it appeared that i just had to reboot the router). so i entered some commands in the terminal (don't really remember now which ones) which i googled.

as a result now i have no internet, no Network Manager icon on the top right corner, and when i go Settings=>Network it says "Oops, something has gone wrong. Please contact your software vendor. NetworkManager needs to be running." when i load Ubuntu from USB stick it's there and works fine.. 

i run Ubuntu 18.04.5 LTS 32-bit ASUS P81IJ if this helps...

any recommendations?

thank you,
Alex

---

### Post by CelticWarrior on 2021-01-24
> [COLOR=#000000]i run Ubuntu 18.04.5 LTS 32-bit ASUS P81IJ if this helps...[/COLOR]

[COLOR=#000000]any recommendations?[/COLOR]
The computer has 64-bit hardware so the recommendation is to take advantage of this opportunity and just backup and reinstall 64-bit Ubuntu.
Then avoid using commands that you googled somewhere and don't really remember later when you don't know what you're doing. If you have any problem ask here first.

---

### Post by podobin on 2021-01-25
thank you for your reply Changan CelticWarrior! this was not the solution i was looking for, but looks like i'll have to do it..
[COLOR=#DD4814][[COLOR=#000000]CelticWarrior[/COLOR]]("https://ubuntuforums.org/member.php?u=1826209")[COLOR=#000000][CelticWarrior]("https://ubuntuforums.org/member.php?u=1826209")[/COLOR][/COLOR]

---

### Post by podobin on 2021-01-25
> **CelticWarrior said:**
> The computer has 64-bit hardware so the recommendation is to take advantage of this opportunity and just backup and reinstall 64-bit Ubuntu.
Then avoid using commands that you googled somewhere and don't really remember later when you don't know what you're doing. If you have any problem ask here first.

hey, i see here [yum - What is the difference between i686 and x86_64 packages? - Unix & Linux Stack Exchange]("https://unix.stackexchange.com/questions/158244/what-is-the-difference-between-i686-and-x86-64-packages")  that my i686 "[COLOR=#242729][FONT=Arial]Technically, i686 is actually a 32-bit instruction set (part of the x86 family line), while x86_64 is a 64-bit instruction set (also referred to as amd64)." 

[/FONT][/COLOR]are you sure 64-bit Ubuntu will work on my system? can you recommend which one? (i have 4 gb ram)

thank you!

---

### Post by CelticWarrior on 2021-01-25
Is this your laptop? -> [https://www.notebookcheck.org/Asus-P81IJ.32818.0.html](https://www.notebookcheck.org/Asus-P81IJ.32818.0.html)
If so, it has [this CPU]("https://ark.intel.com/content/www/us/en/ark/products/36697/intel-core-2-duo-processor-su9400-3m-cache-1-40-ghz-800-mhz-fsb.html"). As usual, you can install a 32-bit OS in 64-bit hardware but not the other way around.
Due to hardware's age and limitations prefer a lightweight distro like Xubuntu or Lubuntu. The standard Gnome based Ubuntu is too much for that (but works, albeit slowly).

---

### Post by podobin on 2021-01-27
thanx CelticWarrior! installed Lubuntu along with Ubuntu, looks like it works.. but i like my Ubuntu more.. maybe someone can help me with restoring NetworkManager in my Ubuntu? a bit busy now, tomorrow i will look back to my google searches and memory and will post here which commands i entered to terminal which caused NetworkManager to disappear...

---

### Post by podobin on 2021-01-28
emmm.. so i don't really remember which commands i entered to terminal.. but if anyone has any suggestions how to fix my issue, would be much grateful!

---

### Post by coffeecat on 2021-01-28
> **podobin said:**
> emmm.. so i don't really remember which commands i entered to terminal..

You don't have to remember. The system does the remembering for you. Either...

1 - Open a terminal and press the up arrow key repeatedly to view all your previous terminal commands from the most recent backwards.

Or...

2 - Open the hidden file in your home folder called .bash_history.

I'm assuming you know what a hidden file is and how to open it in a text editor. If not, post back and someone will be able to help you.

If you can find the relevant commands and post them, perhaps someone will be able to say what went wrong.

---

### Post by podobin on 2021-01-30
> **coffeecat said:**
> 
Or...

2 - Open the hidden file in your home folder called .bash_history.

```
sudo apt-get update 
sudo apt-get dist-upgrade
nm-tool
sudo tee /etc/NetworkManager/conf.d/wifi.scan-rand-mac-address.conf > /dev/null <<EOF [device]
wifi.scan-rand-mac-address=no
EOF

sudo service network-manager restart
sudo start network-manager
$ ps -p1 | grep systemd && echo systemd || echo upstart
sudo start networkmanager
sudo ip addr
nmcli help
sudo tee /etc/NetworkManager/conf.d/wifi.scan-rand-mac-address.conf > /dev/null <<EOF [device]c
c
service network-manager restart
service network-manager status
m
nm-applet
sudo /etc/init.d/NetworkManager restart
sudo /etc/init.d/NetworkManager start
~$ root
sudo NetworkManager
sudo NetworkManager start
sudo service network-manager start
cat /etc/network/interfaces

cat /ec/network/interfaces
sudo gedit /var/lib/NetworkManager/NetworkManager.state
sudo systemctl enable NetworkManager.service
start network-manager
network-manager
sudo apt update
sudo apt dist-upgrade
```

should be in here..

waiting for the next good samarithan..:)

---

### Post by podobin on 2021-01-30
forgot. thank yu, [**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=129087")!

---

### Post by podobin on 2021-04-17
hello.. is there anybody out there?...

---

