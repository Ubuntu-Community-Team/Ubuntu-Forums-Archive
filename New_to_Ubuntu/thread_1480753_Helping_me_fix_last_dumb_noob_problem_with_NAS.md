---
title: "Helping me fix last dumb noob problem with NAS"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by sb5551 on 2010-05-11
Hey y'all. I am loving everything now that all my kinks are worked out except when I try to connect to my NAS drive. In 9.10, I used to places>conncect to server and click FTP with login. I would type in the network address and my name (admin) then I would be asked for a password and it would mount right to my desktop. Everything was there, things were great and I almost dropped windows out the window. 

I decided to wait till 10.04 just in case. I have all the little bugs worked out except now when I do the following steps get the folders mounted, but when clicking on them get this error :Sorry, could not display all the contents of "/ on 192.168.1.8": Unexpected end of stream. The folder still mounts to my desktop, but I click on it and get that error:mad:. Please help me. I didnt install anything in 9.10, it just worked, so I don't know what s going on here. Do I need this samba things. The NAS drive is a 1Tb and my computer wired directly to the router the NAS is to. 

Thanks

---

### Post by CharlesA on 2010-05-11
What brand/model/type is the NAS?

Is it using just straight FTP, or does it uses Samba to access the data?

---

### Post by sb5551 on 2010-05-12
Charles,
  Sorry for the delay in response. It is a black armor seagate 1 TB drive. I am guessing it uses FTP since in ubuntu 9.10 when I could connect to it I just used the connect to server as FTP with login. I never configured anything it just worked, now in 10.04 it doesn't work. I am guessing that means that I didn't use Samba either because I never configured anything.
 
On my gf's mac or windows, I just click to the network and the drive is there. Its connected via cable directly to the router no wireless involved.

---

### Post by sb5551 on 2010-05-13
Anyone?

---

### Post by sb5551 on 2010-05-13
I found out that it can be connect to through NFS, but tried and managed to get it to connect and get me the same message as said in my first post.

---

### Post by sb5551 on 2010-05-14
And, I fixed it. It was my own fault. Aparrently, I made a typo when setting the static ip address and was trying to connect to the wrong place.

---

