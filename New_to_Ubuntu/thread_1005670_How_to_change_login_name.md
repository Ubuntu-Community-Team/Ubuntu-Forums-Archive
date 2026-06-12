---
title: "How to change login name?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Inquisitorthemad on 2008-12-08
I foolishly allowed ubuntu to default to using my real name as my login name. I now want to change this so I don't go by my real name in Wesnoth servers. What I want to know is HOW DO I DO IT?!

I searched Google first thing. One thread recommended System->Administration->Users and Groups. It allowed me to change everything EXCEPT MY USERNAME. I saw another thread recommending usermod in the terminal. THIS DIDN'T WORK.

Please. How do I do it?!

---

### Post by lovelyvik293 on 2008-12-08
I think that you can't change a user's name.You can make a new user and then delete the user you don't want.

---

### Post by gettinoriginal on 2008-12-08
Try this: :p

[http://sudan.ubuntuforums.com/showthread.php?t=945461](http://sudan.ubuntuforums.com/showthread.php?t=945461)

---

### Post by banerjeerupak on 2008-12-08
create a new user by going to System -> Administrator -> Users and Groups

Give this user the name you want on the wesnoth servers.

---

### Post by The Cog on 2008-12-08
I think the user's name is only stored in 3 files - /etc/password, /etc/shadow and /etc/group. You could use search and replace on these 3 files. Back them up first!!! Oh, and rename your /home/? directory too.

I did it once. But then discovered that evolution saves the full path including the username in lots of its config files. It took me ages to track down and replace every reference to the old directory. Most other applications aren't that brain-dead though.

---

