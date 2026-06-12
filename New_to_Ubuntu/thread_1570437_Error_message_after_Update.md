---
title: "Error message after Update"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Peterfc on 2010-09-08
When i get an Update to install from the Update Manager i always get an error message when the update is done.

The only way i can find to enclose the error message is by an attachment.

Thanks for reading my problem

---

### Post by DougieFresh4U on 2010-09-08
> **Peterfc said:**
> When i get an Update to install from the Update Manager i always get an error message when the update is done.

The only way i can find to enclose the error message is by an attachment.

Thanks for reading my problem
Not sure what is happening there, but lets try terminal:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

---

### Post by Peterfc on 2010-09-08
Hi DougieFresh4U

Thanks for your reply. I have done as you advised now i just neeb to wait for the next Update but i am sure that what you advised will have worked fine.

Thanks

Peter

---

### Post by DougieFresh4U on 2010-09-08
> **Peterfc said:**
> Hi DougieFresh4U

Thanks for your reply. I have done as you advised now i just neeb to wait for the next Update but i am sure that what you advised will have worked fine.

Thanks

Peter
I am not saying 'Don't use update manager' but I always recommend using terminal for updates. Also have you checked to see what updates in Software Sources are enabled?
Of course the ole update grub from terminal
```
sudo update-grub2
```

---

