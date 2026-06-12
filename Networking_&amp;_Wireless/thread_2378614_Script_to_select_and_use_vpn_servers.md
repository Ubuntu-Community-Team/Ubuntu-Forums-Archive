---
title: "Script to select and use vpn servers"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by sushi-addiction13 on 2017-11-25
I put this together a few years ago because I needed to;
- select any server from a big list of ovpn files
- switch to any server whenever
- update all servers by replacing with new set of ovpn files frequently
- easy to adapt for use of script on other machines (copy & paste whole directory with script and ovpn files)


Is there a better way? Anyone seen/have a script for something like this for openvpn?
I'm not happy about editing /etc/sudoers


I get the feeling there must be something better out there because debian variants and probably other distros don't allow you to easily add a huge list of ovpn files. You can only enter them manually which takes forever.

I've looked but all I get is how to set up a server :(

ovpnlist.sh (script, sound file, ovpn files and user/pass file are all in config dir)
```


#!/bin/bash
cd "$(dirname "$0")"
#Set working directory to script directory
#Added after adding "baka ALL=(ALL) NOPASSWD: /home/baka/VPN/config/opvnlist.sh" to /etc/sudoers so system password not needed. Otherwise sudo needed to run ovpnlist.sh

sed -i 's/auth-user-pass$/auth-user-pass ovpnp/g' *.ovpn
#$ is to dectect new line. Adds user/pass file(ovpnp) to all ovpn files (safer than command line option)

printf '\033[8;54;170t'
#Resize terminal window. 54 is lines height, 170 is lines width

echo "Ctrl+C to pick a new server."
echo "Press Ctrl+C twice to exit"
sudo openvpn --script-security 2 --config au11.vpn.com.udp1194.ovpn --up /etc/openvpn/update-resolv-conf --down /etc/openvpn/update-resolv-conf --auth-retry nointeract

xdotool search --class "terminal" windowactivate %@
#Window to foreground on disconnect

mpg123 -g 20 retro_game_jingle.mp3 &
select FILENAME in *udp.ovpn;
do
     echo -e "\033[31m Selected $FILENAME ($REPLY) \033[30m"
     sudo openvpn --script-security 2 --config "$FILENAME" --up /etc/openvpn/update-resolv-conf --down /etc/openvpn/update-resolv-conf --auth-retry nointeract
     echo -e "\033[31m Closing $FILENAME ($REPLY) \033[30m"
     sleep 1
     killall openvpn
     xdotool search --class "terminal" windowactivate %@
     mpg123 -g 20 retro_game_jingle.mp3 &
     echo "Press Enter to relist servers."
     echo "Enter the number of the vpn you want to connect to"
     echo "Ctrl+C to pick a new server or exit"
done


```

It's made to be in startup applications or run when needed.
It first automatically connects whatever server. After that a server can be selected.

---

