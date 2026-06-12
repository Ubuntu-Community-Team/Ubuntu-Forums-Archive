---
title: "this is how you install old drivers, don't need new cards"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by lilmale1 on 2008-09-09
the following shows how to install drivers on inf files.
usually you will need a inf and sys. 

try using that for old nic cards


you will have to check the card you have on the system

with command line: lspci
that will tell you what card you have, so look for that so u can
use an old driver from the net. i can help you look for one so tell
me what card you have too.

first you'll use the ubuntu 8.0.4 cd and install
with command: sudo apt-cdrom add
                       sudo apt-get update
                       sudo apt-get install build-essential

after you got build-essential installed, install ndiswrapper-1.53.tar.gz file
to do this you will need that file ndiswrapper-1.53.tar.gz you can get it almost anywhere in linux web sites.

so once you have it. put it in the the computer under the name of the computer. like for example mine is /home/xbatis......so it will be in the directory xbatis.

in terminal put command: su ..............then type in password
if they forget the password. type in command: sudo passwd ....and type in a new password twice
exctract ndiswrapper with terminal. using command: tar -zxvf ndiswrapper-1.53.tar.gz

that will extract the file to the same location that was the computer name.

type command: cd /home/xbatis/ndiswrapper-1.53
remember xbatis is your computer name.

then type command: ndisgtk

it will tell you to install a program that looks how to install like this command: apt-get install ndisgtk .........or something like that
it will tell you what to put

after type command: ndisgtk

that will open the place to install driver for your inf.file.
remember to get a your driver as inf file. otherwise there is no other way for this. go to the place where you saved you inf. file like in directory xbatis just to make it easy to find. click on the inf file and install.

now that it install and you got your driver installed.
go to insternet from another computer and install the wifi radar.

the latest version is the best for wifi radar.
the way to install it is to look it up with a file that end with .deb
that will install it like automaticlly
search on another computer like "wifi radar linux debian"
.deb is short for debian package.
put it in your computer your working on and double click the file
it should open the install page by itself. then install it.

reboot computer and go to applications > internet and it should be there.

after that you wont need to use wifi radar because you will use system
network connections. just click on the little icon on top of your screen where
its the little screen icon to enable wireless if it hasn't done so.
then you will see your network pull down when you click that icon again.

the click on your network and it will automaticlly connect you.

if you want to change setting because it didn't work. go to wifi radar page
click on your network name and edit it with auto option: and shared or wep for your password selection.

that all just click one more time on icon on top of your computer to see if your network connects.

---

