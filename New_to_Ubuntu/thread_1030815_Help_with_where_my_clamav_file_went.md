---
title: "Help with where my clamav file went"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by berri67 on 2009-01-04
I have ubuntu 8.04 LTS and I went to the Synaptic Package and downloaded the clam Av package to my drive.  I did a search and said it went to my home page berri, but I can't find the files.  Does anyone know where it went and how would I find it?

Also, I went to try and move to the proper directory clam av with the command:  sudo mv daily.cvd/var/lib/clamav and then it prompted me for the password, and I was unable to put the password in the place.  Why am I unable to put the password in?  
How do I get program this in the right folder so that it can work?

I want to get this clam av working, what would be the command to update it, once I find it.

Thanks for any help.
berri67

---

### Post by berri67 on 2009-01-04
Also on my terminal it says as follows:  name@name$  It does not say name@name-desktop$.  How do I get it to say this with the desktop.

---

### Post by oldos2er on 2009-01-04
It's normal not to see anything echoed to the screen when you type your password into a terminal. Just type it in and hit Enter.

 You can see where any file in a package has been installed in Synaptic Package Manager. Click 'Status,' 'Installed,' right-click on a package, choose 'Properties,' Installed Files.'

---

### Post by theozzlives on 2009-01-04
```
mkdr /tmp/virus
```
```
clamscan -ri --move=/tmp/virus /home/yourusername
```

---

### Post by berri67 on 2009-01-04
mkdr = command not found.

Is this the right command to make a directory?

How does one make a directory?

Thanks.

---

### Post by berri67 on 2009-01-04
I would like to move the anti-virus to the proper directory but am unable to do so.

I typed:  sudo mv daily.cvd/var/lib/clamav and it says:

mv:  missing destination file operand after 'daily.cvd/var/lib/clamav

Do I put -t here and since I don't have desktop in my home directory where would I put it?

Thanks for any help.

---

### Post by oldos2er on 2009-01-04
> **berri67 said:**
> mkdr = command not found.
  

 mkdir

---

### Post by oldos2er on 2009-01-04
> **berri67 said:**
> I would like to move the anti-virus to the proper directory but am unable to do so.

I typed:  sudo mv daily.cvd/var/lib/clamav and it says:
  

 I think you left out a space:  sudo mv daily.cvd /var/lib/clamav

---

