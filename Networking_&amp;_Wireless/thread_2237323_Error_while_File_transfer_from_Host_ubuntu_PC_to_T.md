---
title: "Error while File transfer from Host ubuntu PC to Target arm Board via ethernet"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by Switesh_Fulpagare on 2014-08-01
Hi,

I am very new to ubuntu, it may be simple query, please guide me.
I want to transfer file from Host PC ( ubuntu instaaled ) to the Target bord ( arm, wandboard booting from SD card) via ethernet port.
Target board is ip address reachable.

Host -
1. $ whoami
    minda
2. $ hostname
    minda-ThinkCentre-Edge71
3. $ ifconfig
    eth0      inet addr:192.168.xx.yy       ==> i am not mensioning actual ip address for security purpose

Target board - 
1. $ whoami
    ubuntu
2. $ hostname
    arm
3. $ ifconfig
    eth1       inet addr:192.168.aa.bb     ==> i am not mensioning actual ip address for security purpose

I want to transfer file 'pascal_triangle'  from  /Target_Board/Switesh directory on Host  to the Target board in the directory /home/ubuntu/bin 

Target board having
username = ubuntu
password = xyz
Target is connected to the serial consol (gtkterm).

from Host PC Terminal i am giving following commands to transfer file to target

1. $sudo apt-get install openssh-server[FONT=Lohit Devanagari]
2.[/FONT][FONT=Lohit Devanagari]$ sudo sshd service restart 
[sudo] password for minda: 
sshd re-exec requires execution with an absolute path
[/FONT]3. [FONT=Lohit Devanagari]$  sudo scp /Target_Board/Switesh/pascal_triangle [EMAIL="arm@192.168.aa.bb"]arm@192.168.aa.bb[/EMAIL]:/home/ubuntu/bin
[EMAIL="arm@192.168.aa.bb"]arm@192.168.aa.bb[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="arm@192.168.aa.bb"]arm@192.168.aa.bb[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="arm@192.168.aa.bb"]arm@192.168.aa.bb[/EMAIL]'s password: 
Permission denied (publickey,password).
lost connection
[/FONT]
So [FONT=Lohit Devanagari]I am getting above error, "Permission denied, please try again.[/FONT]"

Can anyone tell me what is the problem, i am giving correct password xyz, 
then also getting this error. Please tell me possible solution.
or tell me accurate steps to transfer the file.

---

