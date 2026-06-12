---
title: "finding the passphrase in filezilla - how to do it on commandline"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by dilbert_one on 2014-11-30
good day dear ubuntu-experts


i need to find the passwd that is stored in the filezilla configurations


it is stored in plaintext

the background:  i cannot remember the passwd. i need it - for some other purposes. 
i need to have this while i want to set up a ssh tunnel via terminal. This tunnel uses the same ssh passwd-credentials. 


so i need to have the filezilla-passwd.  It is stored in plaintext. 


well for Ubuntu it is in  Linux FileZilla SiteManager file:

```
/home/username/.filezilla/sitemanager.xml 
```

 

but for opensuse - where to fin the passwd for filezilla in opensuse? 

```


linux-70ce:/home # 
linux-70ce:/home # find . -name "filezilla*"

./martin/.filezilla/filezilla.xml
./martin/Dokumente/os_systen_update/filezilla_
linux-70ce:/home # 
linux-70ce:/home #
```  

well now i want to open the xmlfile and read out the passwd

note: well for Ubuntu it is in Linux FileZilla SiteManager file:
      ```


    /home/username/.filezilla/sitemanager.xml linux-70ce:/home # 
linux-70ce:/home # find . -name "filezilla*"

./martin/.filezilla/filezilla.xml
./martin/Dokumente/os_systen_update/filezilla_
linux-70ce:/home # 
linux-70ce:/home #


```


 well now i want to open the xmlfile and read out the passwd

note: well for Ubuntu it is in Linux FileZilla SiteManager file:
      

     ```
    /home/username/.filezilla/sitemanager.xml 


```

i need to find this file -
any and all help is greatly appreciated

---

