---
title: "About my network."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Himself2007 on 2009-11-03
[B][COLOR="DarkOliveGreen"][I]Hello

New user here...
About my network.
I installed Ubuntu 9.10 and found that other Windows XP computers on my network are accessible from Ubuntu. 
Good!
I installed Samba, and configured a new user.
But Samba is not included in my present Windows network but created its own network called "workgroup" in Ubuntu.
But I confirmed I can use any Windows computers to access this "workgroup" network in Ubuntu.
So right now, I'm perfectl bi-directional but using two different network names.
Question : how can I unify these two networks together?
I would like to include Ubuntu's "workgroup" network into my present network so I can deal with only one network name.

Luc[/I][/COLOR][/B]

---

### Post by Darce on 2009-11-03
Possibly why I've always called my windows networks 'workgroup'  ;)

---

### Post by Technoviking on 2009-11-03
You need to edit your samba config.

```
gksudo gedit /etc/samba/smb.conf
```

and change

```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]WORKGROUP[/COLOR]
```

To what ever your Windows workgroup is called
```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]TECHNOVIKING[/COLOR]
```

Then restart samba
```
sudo /etc/init.d/samba restart
```

---

### Post by Himself2007 on 2009-11-03
[B][COLOR="DarkGreen"][I]Hello technoviking and thanks for fast reply!
I don't follow you excatly.
My actual Ubuntu created name is "workgroup".
And suppose my Windows network is called "champion".
And can I figure out from your example?
Thanks![/I]

Luc[/COLOR][/B]

---

### Post by Himself2007 on 2009-11-03
technoviking

OK1 I just figured out and it seems to work bit not perfectly.
I was able to access the network bi-directionnaly and under the same network name.
But if I restart both computers my Windows computer can't see my other Ubuntu computer.
Something i don't understand.
Help...please?

Luc

---

