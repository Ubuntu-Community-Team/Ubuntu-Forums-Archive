---
title: "Question to NFS and Samba for current setup"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by hovzio on 2008-07-09
Hello, I'm trying to set up a little network and well.. please bare with me. I've got two laptops, one with Hardy Heron and the other with eeeXubuntu, basically xubuntu 7.10. (A little trim down and touch up for the eeepc, cool stuff considering the distro it came with..) I'm using some no name brand wireless router provided by my isp and its set up for dhcp. Now I've got a couple of books here and I've read a bit of basics but a couple of questions remain unanswered. For starters I just want to be able to exchange files and play around with ssh logins and so on. Especially access my music drive using the eee. 

I've read a little about NFS and Samba and understand the bare concept. All the books I gotten seem to assume that I'm using a linux box as a dhcp server, firewall etc, I'm using a wireless router. When I go into network with the file manager it shows a little icon, "Windows Network". To my question; does this mean that I have to use Samba?? What is this "Windows Network" icon? Does the router have anything to do with the type of network I set up? I'm kinda guessing it depends more on client/server setup but have no clue.. I assume NFS would be more appropriate since there aren't any windows pc's here. 

Decided to check out networking and just have some fun with it, well I've managed to ping the laptops but thats about it. Appreciate any input and tips as well as where I can find more info on "where to go from here" (books, links, etc..) Thanks:)

---

### Post by dmizer on 2008-07-09
to share files between your ubuntu machines, see the 4th link in my sig.  samba is way more complex to set up, and is specifically for sharing files with windows machines.  if you don't have a windows machine, you don't need samba.

to use ssh, simply install the ssh server on both machines:
```
sudo aptitude install openssh-server
```
then you can use the following command to ssh:
```
ssh username@ipaddress
```
where username is the username on the remote computer, and the ip address is the remote computer's ip address.  for example, if you wanted to ssh from your hardy box to your eeeXubuntu box:
```
ssh eeeXubuntu-user@eeeXubuntu.ip.address.here
```

---

### Post by hovzio on 2008-07-10
Thanks!!! Do you know what this little windows icon is all about in my network tab in nautilus? That really threw me off. Thanks again, big help :)

Edit: ssh works!great, I have no problem connecting within my lan but what if I am somewhere else. Do I add my "external" ip and then specify my "internal" ip. (sorry lack of words) The next issue is that my ip changes once a day but I think I'll figure that one out later.

---

### Post by dmizer on 2008-07-10
i don't know anything about setting nautilus up for file sharing.  i believe it's configured to work primarily within windows networks.

if you want to access your files from remote, you will have to use a file system designed for external access.  neither samba nor nfs are designed for that.  i highly suggest you look into using ssh for remote access.

---

