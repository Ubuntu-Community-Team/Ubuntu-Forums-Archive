---
title: "Wine Virus"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-02-28
Hey.... Say i get a windows virus on my Linux computer and i have wine installed. Would the virus run when its fully downloaded or when i click on it to run. if u could tell me that would be great.:popcorn:

---

### Post by ad_267 on 2009-02-28
You would probably have to run the virus yourself.

There's a good article here: [http://www.linux.com/feature/42031](http://www.linux.com/feature/42031)

---

### Post by Ravernomina on 2009-02-28
As in me physically click on the virus and running it? i KNow its a durr.... but making sure :lolflag:

---

### Post by albinootje on 2009-02-28
> **Ravernomina said:**
> As in me physically click on the virus and running it?

Yes.

Although MS-Windows in general has (or had?) the active-x, and autorun "features" which make the live of viruses much more pleasant in MS-Windows.
But does Linux+Wine support "autorun" ? I guess not.

---

### Post by Ravernomina on 2009-02-28
Thats right u can turn of active X controls :3 hehe :P:popcorn:

---

### Post by computerfreak on 2009-02-28
i don't think it will work because you have to actually run the virus yourself, and it would only ruin wine folder. which could cause some damage, but i don't use wine much. and it would ruin your ubuntu files because it wont those those formats and would know where to look unless it where a linux virus.

---

### Post by bodhi.zazen on 2009-02-28
There are reports of viruses running in wine.

[http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/](http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/)

These viruses can infect your wine installation , or fake C drive, and shared files or directories.

IMO you should do 3 things.

1. [color=red][size=4]DO NOT RUN WINE AS ROOT[/color][/size]

2. In your ~/.wine remove ALL LINKS outside of the ~/.wine directory. This includes a link to / and a link to your home directory.

3. Use Apparmor to confine wine. This is a little more complicated, but this is exactly what apparmor is designed to do.

---

