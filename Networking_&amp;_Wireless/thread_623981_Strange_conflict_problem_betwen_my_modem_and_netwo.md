---
title: "Strange conflict problem betwen my modem and network card"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by simion314 on 2007-11-26
Hi,  i connect to internet using dial up(a phone with modem).
If i enable the network card to connect to a LAN(other computer in my home) after restarting the modem will not connect. I have no message error or something like that, the phone shows that is connected for 20 seconds then it closes the connection.
To make the internet to work again i must disable the network card. The changes applys only after reboot,  i can't make it work without rebooting.

I start the dial up from this script:
#######################################
#!/bin/sh
     SPEED=230400
     TTY=/dev/ttyUSB0
     ISP=zapp
     USER=zapp
     pppd $TTY $SPEED \
             defaultroute \
             lock \
	     modem \
             name $ISP \
             user $USER \
             debug kdebug 1 \
             connect '/usr/sbin/chat -v -s -f /etc/ppp/chat-sprintpcs'
########################################
there are other 3 files asocieted with this script:

chap-secrets
##########################################
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
#"tttttttt"	*	"fdsds"
zapp 		* 	ttt
##########################################

chat-sprintpcs:
#################
ABORT "NO CARRIER"
     ABORT "NO DIALTONE"
     ABORT "ERROR"
     ABORT "NO ANSWER"
     ABORT "BUSY"
     '' AT+crm=1
     OK ATDT#777
     CONNECT
#################

options
#########
lock
#######

This scripts are found in /etc/ppp( the intenet provider said to place this scripts here replace the existing one) the other files are at default.

in the instalation i edited the /etc/resolv.conf and added the ip addres of the server

I want to enderstend why the internet will not work when i enable the network card and how can i fix it. I ask you the explanation and the solution(not only the solution).
Hope someone can help me. Thx

---

