---
title: "Back up script"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-08-19
I have written a little backup script, it works over my little network at home. However when I run it, I have to enter my password to ssh into the other machine multiple times. Is there some way I can set this up so I just enter the password once?

Here is the script:
```
#!/bin/bash
rsync -avz -e ssh ****@192.168.0.2:/home/****/Deakin/ /home/****/Deakin/
rsync -avz -e ssh ****@192.168.0.2:/home/****/programming/ /home/****/programming/
#rsync -avz -e ssh ****@192.168.0.2:/home/****/Ubuntu One/ /home/****/Ubuntu One/
rsync -avz -e ssh ****@192.168.0.2:/home/****/windows/ /home/****/windows/
rsync -avz -e ssh ****@192.168.0.2:/home/****/Documents/ /home/****/Documents/
rsync -avz -e ssh ****@192.168.0.2:/home/****/movies/ /home/****/movies/
```

Also how do I get it to recognize Ubuntu One as a directory?

Cheers Mick Carey

---

### Post by HPD2 on 2010-08-19
> **Mick8882003 said:**
> I have written a little backup script, it works over my little network at home. However when I run it, I have to enter my password to ssh into the other machine multiple times. Is there some way I can set this up so I just enter the password once?

Also how do I get it to recognize Ubuntu One as a directory?


```
#!/bin/bash
rsync -avz -e ssh ****@192.168.0.2:/home/****/Ubuntu\ One/ /home/****/Ubuntu\ One/ 
```Not sure about the password thing but you could try the above code.

---

### Post by silverglade00 on 2010-08-19
If you use a public key, you won't have to enter the password at all.

[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

You also need to escape the space character in both parts of the rsync command. 
```

#!/bin/bash
rsync -avz -e ssh ****@192.168.0.2:/home/****/Ubuntu**\** One/ /home/****/Ubuntu**\** One/

```

---

