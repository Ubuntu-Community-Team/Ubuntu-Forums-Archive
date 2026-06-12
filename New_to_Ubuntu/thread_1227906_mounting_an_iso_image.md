---
title: "mounting an iso image"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by dharanitharan on 2009-07-31
hi frenz,
           tell me how to mount an iso image..:)

---

### Post by MelDJ on 2009-07-31
open with archive manager to view files

---

### Post by ukripper on 2009-07-31
in terminal u can use this:
```
sudo mount /path/to/iso -o loop /place/to/mount
```
replace above accordingly.

---

### Post by dharanitharan on 2009-07-31
no.. i want to mount not to view the files.... in windows we ve deamon tools know .. lik that:)

---

### Post by dharanitharan on 2009-07-31
place to mount in the sense
:)

---

### Post by RomeReactor on 2009-07-31
Hi. To do that with a graphical interface, you can use GmountIso. It's in the repositories, so you can find it searching in Synaptic, Add/Remove, etc.

---

### Post by rsiddharth on 2009-07-31
> **dharanitharan said:**
> place to mount in the sense
:)
"Place to mount " is the location where you wish to mount the .iso image . 

If your using ubuntu 9.04 , then most of the external media that you insert (viz,pendrive , cd ROM , etc ) gets mounted inside a folder under " media ' folder which is located in " / " ( i.e the root folder ) .

If you know how to go to the root folder ,its well and fine , in case your not aware ,here is how you go - Places -- > Home Folder . 

* Now your in the Home Folder .
* hit ctrl+L and you must see a location bar materialize . you will probably see something    like " /home/youraccountname"    . 'youraccountname' is the name that you provide while you log in for a session in ubuntu . 
* clear the location bar and type " / " ,though without the quotation and hit enter(or return) .
*Now you search for a folder called 'media' and your there ! .

If you wish to mount your iso image here , as ukripper as said you got to type(in terminal ) 
```

sudo mount /path/to/iso -o loop /place/to/mount 
```here 
```

 /path/to/iso
``` will be the destination where you have placed your iso image . 
 for instance if you have placed it in your " Documents " folder , then the  path will be 
```

/home/youraccountname/Documents/nameofiso.iso  

```Coming to the second part :
```

/place/to/mount
```Assuming that you intend to mount your iso image under the 'media' folder about which I described above , the code will be something like this : 

```

/media/cdrom0

```your iso gets mounted in cdrom0 folder which under 'media' folder ! .

---

