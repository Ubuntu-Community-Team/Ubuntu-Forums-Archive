---
title: "How to paste a file content into xterm by script?"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-29
Hello, I would like to paste a file content into xterm by script, using xsel or xclipboard or whatever works. What are the alternative programs since they are not intended for that :(

---

### Post by Christmas on 2010-11-29
Hi. I'm not sure I understand your question. You can use **cat filename** in a Bash script, and it will show the content of the file. You can also use pipes in the script to grab the output and parse him or do whatever you want e.g. **cat filename | grep Ubuntu** will show only the lines that contain the term "Ubuntu" (case sensitive).

---

### Post by honeybear on 2010-11-30
> **Christmas said:**
> Hi. I'm not sure I understand your question. You can use **cat filename** in a Bash script, and it will show the content of the file. You can also use pipes in the script to grab the output and parse him or do whatever you want e.g. **cat filename | grep Ubuntu** will show only the lines that contain the term "Ubuntu" (case sensitive).

I was thinking in a way:
```

echo "Hello" > /tmp/myfile
echo "Bye" >> /tmp/myfile
echo "Click on xterm"
sleep 10s 
cat /tmp/myfile | pastetoX11
# or
cat /tmp/myfile | xsel --clipboardtox11


```

something like that

---

### Post by earthdan on 2011-06-15
how to use **xclipboard** from command line??

---

### Post by uRock on 2011-06-15
Try ```
man xclip
``` in a terminal. If you need guidance with this, then please start a new thread, instead of awakening old threads.

Thread Closed

---

