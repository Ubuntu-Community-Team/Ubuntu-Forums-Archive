---
title: "Terminal"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by p.caraglio on 2011-06-02
My question regards the terminal in ubuntu. Is there any way to get the terminal to start off in a different directory then the default? For example I always start off in the directory with desktop, downloads, etc, but I want to start off in another directory (let's call it mystuff for simplicity's sake) how would I go about doing that. I do know about the change directory (cd) feature but I want to be able to always start off in mystuff so I don't always have to type "cd mystuff" every time I turn on my terminal. As a side note I am using ubuntu 11.04.

---

### Post by Mariane on 2011-06-02
If you use Konqueror you can right-click on the folder and select "Actions" and then "Open Terminal Here". 

Mariane

---

### Post by frankbooth on 2011-06-02
One way to do it is by adding a command at the end of ~/.bashrc

**Example:**
```

echo "cd Desktop" >> .bashrc

```
We added 'cd Desktop' (make sure this is added to a new line) and as a result the terminal will start at ~/Desktop instead of ~/

**EDIT:** 
just add 'cd /to/your/stuff' instead of 'cd Desktop'

---

### Post by Legendary_Bibo on 2011-06-02
where is your stuff?

---

### Post by p.caraglio on 2011-06-02
Thank you frankbooth! It worked like a charm. What exactly is that file anyways?

---

### Post by Mariane on 2011-06-03
.bashrc is a file with default instructions given to the bash terminal. It is in your /home/username directory. 

Mariane

---

### Post by hakermania on 2011-06-03
```
sudo apt-get install nautilus-open-terminal
```
it provides you this option:
[IMG]http://img545.imageshack.us/img545/197/screenshotwic.png[/IMG]

---

