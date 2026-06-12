---
title: "questions about the grub installer"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-05
i have a question about what shows up on my grub.  It shows two actual ubuntu installs. I am in the process of downloading kgrub so that i can get a screen shot of what it shows.  The fist instance when you click on it.  it hangs up on the login screen the mouse and the keyboard youdo not work at all.  Then just below that you have the repair feature. then you have a second instance of ubuntu in which everything works and then the repair feature for it.  and then under other os's you have my vista business.  

My question is why is there two instances of ubuntu.  And if that is correct and its suppose to have that how do i get in to that into that instance and repair it if the mouse and keyboard is not working?

Kgrub will be installed here with in the next 10 minutes or so.  Once it is installed i will post a screen shot of whats showing in the grub.

Trinidad

---

### Post by trinidadflores on 2009-03-05
as promised here is the screenshot of the kgrub for the above question.

Trinidad

---

### Post by maybeway36 on 2009-03-05
That always happend with Ubuntu. The second one boots into the same Ubuntu system, but with a different version of the Linux kernel. If you want to get rid of it, you can go into Synaptic and remove the old kernel, but if you remove them both you won't be able to boot.

---

### Post by Philip550c on 2009-09-15
everytime the kernel is upgraded it adds a new entry. You can do what the person above me said or you can just remove the old kernel grub entry in kgrub. (Note: This does not remove the kernel, just the grub entry)

---

### Post by hyperAura on 2009-09-15
u can edit menu.lst and try commenting out the entry u say that is not working by placing a # in front of each line..

---

