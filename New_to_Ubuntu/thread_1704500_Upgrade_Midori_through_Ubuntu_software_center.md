---
title: "Upgrade Midori through Ubuntu software center?"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by bbqsandwich on 2011-03-10
Hello!
I installed Midori through the Ubuntu Software Center and I see that it is version 0.2.2. However Midori's website says the latest is 0.**3**.2. Is there a way to keep it updated through the software center?
Thank you in advance?

---

### Post by wojox on 2011-03-10
No not until they decide to update it in the repo's, which may not happen depending on what version of ubuntu your using. Have you looked for a ppa on Launchpad?

---

### Post by NightwishFan on 2011-03-10
Ubuntu freezes packages during every release. You could find a repository with an upgraded version or wait for the next version of Ubuntu. Here is a list of PPAs about Midori:
[https://launchpad.net/ubuntu/+ppas?name_filter=midori](https://launchpad.net/ubuntu/+ppas?name_filter=midori)

---

### Post by bbqsandwich on 2011-03-10
Thanks for the info! (And NightwishFan, I am also a fan! :D) I will look into adding the PPA; it's something I haven't done before so it should be a good learning experience.

---

### Post by NightwishFan on 2011-03-10
You can add a ppa with the terminal using:
```
sudo apt-add-repository nameofppa
```

Remember to refresh the package list:
```
sudo apt-get update
```

Have fun! :)

---

### Post by bbqsandwich on 2011-03-11
Cool, it works! I did

```
sudo add-apt-repository ppa:midori

```

and also

```
sudo add-apt-repository ppa:webkit-team/ppa
```

because the Midori one said that was required. Then

```
sudo apt-get update
sudo apt-get install midori
```

and it upgraded to 0.3.2. It's a lot different, too. There's a New Bookmark button on the toolbar and the menu is condensed into a button instead of a toolbar.

Thanks for all your help!

---

### Post by NightwishFan on 2011-03-11
Enjoy! ):P

---

### Post by maureenc on 2012-02-08
Can I just add a big "Thank You" for the information in this thread which has been really useful to me...... I've just loaded Midori as per instructions...... If only all things in life were so simple!

Thank You

---

