---
title: "yet another ndiswrapper problem"
date: 2005-07-13
forum: Networking &amp; Wireless
---

### Post by fishmonger12 on 2005-07-13
I've been following the information provided in the [ubuntu wiki](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu?highlight=%28amd64%29%7C%28ndiswrapper%29) on how to install ndiswrapper on ubuntu amd64. i get up to the point at which you install the windows driver using the ndiswrapper -i command. at this point it just lists options for me to select, as if ndiswrapper -i wasn't a valid command. but when i do the next step, ndiswrapper -l, it shows the driver i just installed, but says invalid driver next to it. i've been looking at other directions for setting up ndiswrapper and they all mention an .inf file, which is not included with my driver and the wiki gives no information on how to create it. any help is appreciated

---

### Post by bcashman on 2005-07-14
Hi, I just went through this and got it to work. The driver you are looking for should have come with the device you are using . there should be a .inf file, a .cat file and a .sys file. They need to all be in the same folder on your drive. The .inf file is the driver you need to install with ndiswrapper -i, and it needs to be put in quotes just like in the wiki. You will have to remove the other driver you installed first. It took me a while to get it right, but once i did everything worked fine.

---

### Post by fishmonger12 on 2005-07-18
thanks for the help, i found the files you speak of, and now i'm going to try installing them. i downloaded the package off of the linksys website, thinking that's what i needed, but i needed to extract it first >_X.

ok. on doing ndiswrapper -m, i get this error:

modprobe config already contains alias directive

ndsiwrapper -l nets a driver present, hardware present message, which i suppose means i've installed it correctly so far. when i go to networking administration there is no wireless connection listed. same when i go to iwconfig. any ideas?

---

