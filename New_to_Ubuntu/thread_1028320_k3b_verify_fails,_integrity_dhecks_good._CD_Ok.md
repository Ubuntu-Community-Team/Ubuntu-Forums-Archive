---
title: "k3b verify fails, integrity dhecks good. CD Ok?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by 45acp on 2009-01-02
I burnt a CD of kubuntu using k3b. When k3b showed errors when it verified the burn. I inserted the cd and did an integrity check. The cd checked ok. I am not sure how to check the md5sum once the iso has been burned to the cd. How do you do this?

---

### Post by azc on 2009-01-02
Yeah, k3b always does that to me too, even though the burns were successful. There is a bug report on this, but apparently still exists. 

Anyway, this page should be of help:

[http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning](http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning)

I just use the CLI to burn and verify, and don't bother with any front-end GUIs anymore. 

Takes a little getting used to, but well worth the effort IMHO. (Also, CD-RWs are good for practice :D.)

HTH

---

### Post by 45acp on 2009-01-02
Azc, thanks for the reply and the link.

---

### Post by 45acp on 2009-01-02
Question- How come k3b,Brasero and Gnome Baker burn disks that do not verify but using this terminal command "cd /media/cdrom0 && md5sum -c md5sum.txt" the cd checks ok?

---

