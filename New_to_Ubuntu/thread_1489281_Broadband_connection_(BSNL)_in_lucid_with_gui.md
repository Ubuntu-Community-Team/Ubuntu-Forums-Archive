---
title: "Broadband connection (BSNL) in lucid with gui"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-05-20
Recently I tried to connect to internet via Broadband (BSNL, India).  Below are the things 
that I did to make it work. Hopefully, it will help others. Comments,  suggestions are 
most welcome.

_Broadband via cli_

Connect the broadband cable and wait for a couple of seconds before  typing
the command

    ```
sudo pppoeconf
```Answer the simple questions mostly via  "yes". Supply your broadband username and password when asked for. Once  it starts, check pppoe log via the command

    ```
plog
```Also add yourself to "dip" group 

```
sudo adduser username dip
sudo adduser username dialout
```Now you can "connect" and  "disconnect" from broadband via the commands

```
pon dsl-provider
poff
```respectively. I had to reboot once before I could use the  above commands without 
root privileges.

[U]Troubleshooting:
[/U]If after reboot, broadband connection is not up even after using
    ```
pon dsl-provider 
```command, try using the commands
    ```
poff
    sudo ifconfig eth0 up
    pon dsl-provider 
```If this works, it means your eth0 was not up  for some reason during boot
time. So that one doesn't have to use the "ifconfig eth0 up" command 
everytime after reboot, one can open the file "/etc/rc.local" as root  and 
insert the line
    ```
ifconfig eth0 up
```before "exit 0".

For more troubleshooting, check [here]("https://help.ubuntu.com/community/ADSLPPPoE").

_Broadband with GUI_
I was surprised to find no gui for connecting to broadband (correct me  if I
am wrong.) gnome-network-admin (which isn't installed via default)  doesn't
have a "connections" tab anymore!!! According to 2 bug reports, this is  not
a bug at all, but gnome-network-admin has been replaced via  NetworkManager
(which is installed by default).

However, I couldn't find a easy way to connect broadband via
NetworkManager. So I decided to make a small gui using zenity, ifplugd,
pppoeconf. 

```

sudo apt-get install ifplugd zenity pppoeconf

```Save the code below as bb-connect.sh.
```

#!/bin/bash

## Gui for connecting to broadband
## Requires zenity, ifplugd, pppoeconf
## Version: 0.1

## Check if already connected or not
Status=$(plog | tail -n 1 | awk '{print $NF}')

if [ "$Status" == "" ] || [ "$Status" == "Exit." ] ;then
## If not connected

    ## Check if cable is connected or not
    Cable=$(ifplugstatus eth0 | grep detected)
    if [ -z "$Cable" ];then
        zenity --warning --text="Check whether if cable is connected or  not." &
        exit 1
    fi

    zenity --question --title "Broadband" \
        --text "Connect to internet via broadband?"  --cancel-label="Cancel"

    if [ $? -eq 0 ];then
        ## Connecting ...
        pon dsl-provider

        wget --tries=5 "http://www.google.com" \
            -O /tmp/connection.log | zenity --progress \
            --text="Testing network connection..." --pulsate \
            --auto-close --auto-kill --title "Broadband"
       
        JobStatus="${PIPESTATUS[0]}"
        
        if [ "$JobStatus" -eq 0 ];then
            zenity --info --title "Broadband" --text "Broadband  Connected." &
        else
            poff -a
            zenity --warning --title "Broadband" --text "Couldn't  connect." &
            exit 1
        fi

    else
        ## If cancel
        exit 0
    fi

else
## If connected
    zenity --question --title "Broadband" --text "Disconnect broadband?"  \
        --cancel-label="Cancel"

    if [ $? -eq 0 ];then
        ## Disconnecting ...
        poff -a

        if [ $? -eq 0 ];then
             ## Successfully disconnected
            zenity --info --title "Broadband" \
                --text "Broadband disconnected." &
        else
            ## Couldn't disconnect
            zenity --warning --title "Broadband" \
                --text "Couldn't disconnect." &
            exit 1
        fi

    else
        ## If cancel
        exit 0
    fi

fi


```Make the above code executable 

```
chmod +x bb-connect.sh
```and move it to your $HOME/bin  directory. Now you can run it by typing "bb-connect.sh" in the terminal.  If you want to go total gui, then create a bb-connect.desktop file on  your desktop with the following code. 

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=bb-connect.sh
Comment=Connect to the internet 
Name=Broadband
Icon=modem

```You can now just dbl-click on the desktop file to start up your  broadband connection.

---

### Post by dineshs on 2010-05-21
There are modems capable of storing user id and password (Modem in PPPoE mode).You need not use pppoeconf/pon but can directly use web browser once the modem is setup in PPPoE mode.Modems supplied by BSNL can be configured in PPPoE mode.How to do this is explained here
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 

The method suggested by you is `modem in bridge mode'.Regarding the GUI-Very good information.Thanks

---

### Post by a.sarkar on 2010-05-21
To @dineshs
Thanks for the info.
Will look into it.

---

### Post by a.sarkar on 2010-05-22
Couple of edits to the bb-connect.sh script.
Replace the following lines

```

Status=$(plog | tail -n 1 | awk '{print $NF}')
if [ "$Status" == "" ] || [ "$Status" == "Exit." ] ;then

```by
```

ifconfig ppp0
if [ $? -ne 0 ];then

```Also eth0 in the above code, sometimes has to be replaced by eth1, depending on your computer. Check /etc/network/interfaces to know which one your computer is using.

---

### Post by Linuxforall on 2010-05-22
I am on BSNL here in Kalyani West Bengal and have set it up for many others, both router PPPoE and via network manager PPPoE in modem mode, never ever needed CLI as network manager works pretty good, even for PPPoE in modem more, it connects automatically when system is booted.

---

