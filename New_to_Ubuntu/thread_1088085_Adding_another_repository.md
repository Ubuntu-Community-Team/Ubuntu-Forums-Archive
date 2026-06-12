---
title: "Adding another repository"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Jack Campbell on 2009-03-05
Running Ubuntu Intrepid, I am trying to add another repository under synaptic. (The Vodafone Mobile broadband to be precise).
Going thru Package Manager>Settings>Repositeries>Third Party>ADD I get to the panel where I input the URL etc but the ADD SOURCE button is greyed out and I cannot actually get it to save my URL.
Can anyone enlighten me where I am going wrong? (or suggest another way?)

---

### Post by SuperSonic4 on 2009-03-05
I'd use a terminal

```
sudo nano /etc/apt/sources.list
```

opens that file as root, then append your sources to the bottom press ctrl+X to exit (remembering to save) and then ```
sudo apt-get update
```

---

### Post by oldos2er on 2009-03-05
When you add a repository, the line must begin with deb or deb-src.

---

### Post by Jack Campbell on 2009-03-06
Thanks for that. I had twigged the start had to be deb (it said so on the Vodafone website). 
Using the terminal I have managed to add the repo I wanted to synaptic - now it only remains to see if the download/update will work and I can get my netbook going on mobile broadband.

---

### Post by spcwingo on 2009-03-06
After you add the repo don't forget to update apt.  ;)

```
sudo apt-get update
```

---

