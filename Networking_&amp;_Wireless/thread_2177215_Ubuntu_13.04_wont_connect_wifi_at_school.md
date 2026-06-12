---
title: "Ubuntu 13.04 wont connect wifi at school"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by abati2 on 2013-09-27
hy guyz,

Im having a problem trying to connect my laptop to my school´s wifi, the thing is the laptop is able to find my school´s Wifi but when it tries to connect (blinking wifi) within a couple sec´s it says not connected.

But when i use Wifi in my house it works however at school this is not possible.

what i found out is that i can download a certain file that supports different kinds OS based on my school wifi security. so i downloaded a linux version but i dont know how to use that file.

in the attachment you can see a printscreen and the document i download from my school´s web.

i hope that some one can help me out

Laptop: lenovo U410
OS: ubuntu 13.04 with the latest updates

---

### Post by grahammechanical on 2013-09-27
If the wireless adapter in the laptop is able to detect the school wireless access point, then Ubuntu network manager is doing its job. Or part of it. If you are trying to connect to a secure wireless access point the network manager will ask you to authenticate the connection. Are you putting in the correct passphrase or wireless key provided by the school administration?

Network Manager has connection information for your wireless access point at home. It might be set up to automatically connect to the home wireless access point. Now, when you get to school and switch on the laptop Ubuntu loads and tries to connect to the home wireless access point. which it cannot do because you are out of range. Hence, it says disconnected. Is this what is happening?

Have you used the network icon in the top panel to select the school's wireless access point? Did you get asked to authenticate and did you enter the passphrase?

Regards.

---

### Post by abati2 on 2013-09-27
thnx for the reply,

this is not the case, cuz i know the schools wifi and when i trie to connec to it, it asks me for a username and pasword. the username is actualy my scool id and my pasword ofcuzz, when each student tries to log in to the school´s wifi it will autamicly ask for a username and pasword in windows os or mac, 
this is also the same for ubuntu but Ubuntu fails to get a constant connection. each time it tries to connect it says after a couple sec that i am offline

i am 150 % surre that my username and pasword are correct as i tested on a classmates laptop which is on Windows7.

please check my attachment and see what i can do. cuz i dont have an idea

---

### Post by wildmanne39 on 2013-09-27
Hi, have a look here.
[http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss](http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss)
Thanks

---

### Post by abati2 on 2013-09-29
hmm, how can i find the type wireless adaptor I use, and if I might have a package loss ?

---

### Post by varunendra on 2013-09-29
> **abati2 said:**
> what i found out is that i can download a certain file that supports different kinds OS based on my school wifi security. so i downloaded a linux version but i dont know how to use that file.
What you downloaded is a python script to do all the configuration automatically. Usually it is run as "python <name of the .py file>". So assuming that "SecureW2_JoinNow.py" file is on your Desktop, you can try the following -
Open a terminal (Ctrl-Alt-T) and enter following commands-
```
cd Desktop
python SecureW2_JoinNow.py
```

I don't know about python scripts but it seems it downloads a file from "http://wifiportal.hva.nl/php/deploy.phpeduroam/linux/SecureW2.cloudconfig" and saves (after doing some filtering) it as a .pem file in the same directory where the .py file itself is.

These .pem files are nothing but security certificates issued by the organization which you are connecting to. As such, I think you should also be able to get it from your school authorities. Network Manager usually does all the configuration automatically when you connect to a network for the first time and supply the correct ID/password, only this certificate file for enterprise connections needs to be supplied manually.

So if the python script does its job successfully, everything should be done automatically (you should see a .pem file on the desktop or wherever you run the script from). If not, post back and we may be able to do that manually, but I think we shall need that .pem file.

> **abati2 said:**
> hmm, how can i find the type wireless adaptor I use, and if I might have a package loss ?
Like I mentioned above, I think it is a "system-ca-certs" issue, not packet loss. But here is how you find your wireless card and the driver in use -
```
lspci -nnk | grep -iA2 net
```

and to see if there is a packet loss issue -
```
ifconfig
```
..notice the "dropped" value for both TX (transmitted packets) and RX (received packets).

---

### Post by wildmanne39 on 2013-09-29
Did you do what is in the link I gave you? There is a bug in network manager that causes that issue and there is a workaround that should allow you to connect.

You can read the full bug report by going to the link I gave you and clicking on bug in the answer.
Thanks

---

### Post by varunendra on 2013-09-29
Oops! Even I missed the answer part. This is the precise link to Wild Man's answer : [http://askubuntu.com/a/334245](http://askubuntu.com/a/334245)

---

### Post by abati2 on 2013-10-01
guyzz thanxx for the help, i would report you as soon as possible about this !

for this this week a lot off my lecutres are not given, cuz of teachers absence and stuff, so right now im free and probably the coming days too, so i cant test it at the moment. 

i appreciate your work and will difinitly report to you !

---

### Post by abati2 on 2013-10-06
just wanted to say,

previous friday i updated my 13.04 and this time i was able to connect to my school/uni wifi, i was verry happy i thought that the update fixed my problem and i was also getting decent download speed (around 20 MBs).

sadly after like 30 mins it dosconected and from that moment i got the notification saying not able to connect. after that my wifi was trying to connect the whole time with failures.

and guyz about the link you mentioned erlier the bug thing in the wifi ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476)) its a pretty big topic with almost 100 replies and i dont know where to start with cuz each respondent says different things or has different version of linux. i am also not sure if that topic applies to my problem cuz on that friday i was able to connect to my school/uni wifi with their ca_certificate which is (AddTrust_External_Root.pem)

If someone can came up with some logical explanation or way to selve this, please give me some help to fix this issue

---

### Post by varunendra on 2013-10-06
Do you have the "system-ca-certs=" line in your connection keyfile? Check with -
```
sudo cat /etc/NetworkManager/system-connections/*<your connection's name>*
```
Don't post the output here as it also contains your security key if you have saved it. Just see if the "system-ca-certs" line is there. If yes, make sure it is set to false, like this -
```
system-ca-certs=false
```
If it is currently true, you can change it with -
```
sudo sed -i '/system-ca/ s:[Tt]rue:false:' /etc/NetworkManager/system-connections/*<your connection name>*
```

You can get a list of available valid connection names with -
```
nmcli con
```
Just identify the correct one that you use to connect to the school network, and use it in place of ***<your connection name>*** in above commands.

---

### Post by abati2 on 2013-10-07
you are a genius bro it worked out for me finaly ^^ with your method thanxx men.
I also want to thank the others who tried to find a solution for me !

---

### Post by wildmanne39 on 2013-10-07
Your welcome! glad varun was able to help.
Enjoy

---

### Post by varunendra on 2013-10-08
> **Wild Man said:**
> glad varun was able to help
..with the fix originally suggested by you :P

> **abati2 said:**
> it worked out for me finaly ^^ with your method
Very pleased to hear that. Please mark the thread as [SOLVED] now, it helps others looking for help on same issue. Thanks ! :)

---

