---
title: "Gnome Terminal 2.30.2"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by beew on 2010-09-25
I notice that there is no more 'save content' option in Gnome Terminal 2.30.2 so in order to save the terminal output I would have to cut and paste the content to gedit. I wonder if this is a bug or a 'feature', --or maybe the option is hidden somewhere and I miss it?

---

### Post by Kr4zyl3gz on 2010-09-25
Please elaborate on what you mean by "Saved Content"

---

### Post by beew on 2010-09-25
Saving the outputs of the terminal to a document. I think it used to be under "File" in the menu.

---

### Post by lkjoel on 2010-09-25
> **beew said:**
> I notice that there is no more 'save content' option in Gnome Terminal 2.30.2 so in order to save the terminal output I would have to cut and paste the content to gedit. I wonder if this is a bug or a 'feature', --or maybe the option is hidden somewhere and I miss it?
Type this in a Terminal window:
```
cat << EOF > savecontent.sh
#!/bin/bash
echo "Copy and Paste the output of the Terminal window into here:"
echo "When you are finished, press: CTRL+D"
cat > log.txt
echo "Text Saved into log.txt"
EOF
chmod +x savecontent.sh

```
Now type in:
```
~/savecontent.sh
```
every time you want to save your content.

---

### Post by beew on 2010-09-27
Upgraded to gnome terminal 2.31.91 (snatched  from Maverick's repo) 'save contents' is back.

But still, thanks lkjoel for the advice. I am sure shell scripts will come in handy in many occasions.

---

### Post by Clever_Username on 2010-09-27
I swear I learn something new _**every**_ time I browse these forums.

---

### Post by coffeecat on 2010-09-27
> **Clever_Username said:**
> I swear I learn something new _**every**_ time I browse these forums.

Agreed. I've been using Ubuntu and gnome for 5 years and never noticed that feature before. :-k

---

### Post by QLee on 2010-09-27
[QUOTE=coffeecat]Agreed. I've been using Ubuntu and gnome for 5 years and never noticed that feature before. :-k[/QUOTE]
I don't think you've been missing it for years coffeecat, I'm writing this from a Karmic install and my  gnome terminal 2.28.1, doesn't have the feature.

---

### Post by coffeecat on 2010-09-27
> **QLee said:**
> I don't think you've been missing it for years coffeecat, I'm writing this from a Karmic install and my  gnome terminal 2.28.1, doesn't have the feature.

Thanks! I'm glad I haven't been that unobservant. :) I was posting from Maverick and found it in the terminal and thought, "That's handy. Why haven't I seen that before?" 

I was curious to know what the OP was using before to miss it in Lucid, so I booted into a neglected Lucid that was installed from the 10.04.1 disc but not yet updated. The 2.29.6 terminal in that did have the 'save content' option but when I did an update, gnome-terminal was updated to 2.30.2 and 'save content' went AWOL. I'll search Launchpad and see if anyone has filed a bug.

---

### Post by coffeecat on 2010-09-28
Now it's disappeared from Maverick. :(

An update today took the terminal from 2.31.91 to 2.32.0 and 'save content' has gone.

Now you see it; now you don't.

---

### Post by Tibuda on 2010-09-28
If you want to save the output of a command to a file, you can add the ">> filename.log" suffix, like this:
```
ls -l /usr/bin >> lsbin.log
```

---

