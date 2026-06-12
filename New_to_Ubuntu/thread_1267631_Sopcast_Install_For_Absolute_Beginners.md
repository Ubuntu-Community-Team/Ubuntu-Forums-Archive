---
title: "Sopcast Install For Absolute Beginners"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by joshua_james on 2009-09-16
For very new people, anything starting with # is exactly what is to be typed in the terminal (menu>accessories>terminal).  You don't actually type the # in the terminal and where it says, "yourusername," it means your user login on your pc :)

go to menu>accessories>terminal

#sudo apt-get update

#sudo apt-get install libstdc++5

#sudo apt-get install gcc-3.3-base

#sudo apt-get -f install

>go to this site:

[http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)

>choose to save the file to your desktop

#cd /home/yourusername/Desktop

#sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb

>go to this site:

[http://download.sopcast.cn/download/sp-auth.tgz](http://download.sopcast.cn/download/sp-auth.tgz)

>choose to save the file to your desktop

>right-click the icon on your desktop named: sp-auth.tgz

>choose: extract here

#cd /home/yourusername/Desktop/sp-auth

#sudo cp sp-sc-auth /usr/bin/sp-sc

#sudo chown root:root /usr/bin/sp-sc

#sudo apt-get install vlc

>in address bar of Firefox type: about:config

>right click anywhere in the window and select: new and then select: string

>set string name to: network.protocol-handler.app.sop

>set value to: gsopcast

>go to menu>sound and video>sopcast tv player

>in sopcast, click on the: config tab

>clear the text-field beside 'player' then type: vlc

>click: save

---

