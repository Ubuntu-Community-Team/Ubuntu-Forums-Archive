---
title: "trying to set up a vpn on my router getting stuck because of commnds"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by ajoerivera on 2013-10-12
trying to set up a vpn on my router but the the in the guide the only Op has a mac and the commands he refers to obviously dont work. i wouldnt post this material  here but its the commands that are holding me up
 



thanks in advanced this is the [https://www.privateinternetaccess.com/forum/index.php?p=/discussion/1125/asus-rt-ac66u-openvpn-setup-guide-/p1](https://www.privateinternetaccess.com/forum/index.php?p=/discussion/1125/asus-rt-ac66u-openvpn-setup-guide-/p1)
 [COLOR=#333333][FONT=Arial]

"You're almost done. This step might be a bit tricky. We need to put a file called password.txt into the /tmp/ folder [/FONT][/COLOR]*on the router itself*[COLOR=#333333][FONT=Arial]. If you're using windows, you might be able to log into your router using winSCP to log into your modem and have a GUI interface for creating and moving files. If you can do it, great. Create a file called password.txt and in that file on the very first line put your username that PIA sent you (and only your username) and your password (and only your password). Place the file in the /tmp/ folder on your router.[/FONT][/COLOR][COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]I'm on a Mac and I couldn't find software that would successfully ssh into the router, so I did it the old fashioned way. I opened the terminal and typed ssh username@192.168.1.1 and then entered the password when prompted (the username and password you use to log into the router). You should then see a prompt like this: username@RT-AC66U:/#. If you see anything like username@RT-AC66U:/home/root#, you'll need to type in [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]cd ..[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to get yourself to the next higher level until you see only username@RT-AC66U:/#. Once you're there, type[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]cd tmp[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to access the tmp folder. Then type [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]touch password.txt[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to create the password.txt file. If you'd like, you can type[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]ls[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to get a directory listing to make sure it's there. Then you need to type[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]vi password.txt[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to edit the file. [Here is a cheat sheet for using vi]("http://ss64.com/vi.html"). Simply type the letter i to edit the file. Then copy the username PIA sent you on the first line, hit enter then copy your password on the second line. Hit the esc key and then type :wq and hit enter to save the changes and quit the editor. Then type [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]chmod 700 password.txt[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]to change the permissions. Now it's time to go turn on your VPN. Log into your router and go to VPN Server then click on the OpenVPN Client Settings tab. Then toggle the service state from OFF to ON. It'll take a second or two, but it should stay on when it is complete."[/FONT][/COLOR]

---

