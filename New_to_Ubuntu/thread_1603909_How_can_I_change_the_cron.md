---
title: "How can I change the cron?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-10-23
I have a script that I want to be run every X minutes. I already have the cron sentence I need to paste to the cron, but can't find it anywhere.

The terminal command 'crontab -e' works, but it opens it in vim! No way I'm using that yet. How can I edit this file using gedit?

I don't even know the path to the file.

Here's the script:

```
*/3 * * * * /home/sergio/myscript.sh
```

---

### Post by Paqman on 2010-10-23
What version of Ubuntu are you running? The default editor for crontab on recent versions is nano, not vim.

---

### Post by papuccino1 on 2010-10-23
Latest version of Ubuntu. It offers me to use VIM, nano and some other thing, with an arrow pointing at nano saying it's the easiest.

I want to use gedit though.

Thanks for the help. :)

---

### Post by papuccino1 on 2010-10-23
When using this command: 'gedit /usr/bin/crontab' it opens gedit and gives me a 'Could not open' error.

Something related to character encoding. Can anyone help?

---

### Post by CharlesA on 2010-10-23
See here: [http://www.linuxquestions.org/questions/red-hat-31/how-to-change-the-default-crontab-editor-395750/](http://www.linuxquestions.org/questions/red-hat-31/how-to-change-the-default-crontab-editor-395750/)

---

### Post by gmargo on 2010-10-23
At the command line, enter:
```

VISUAL=gedit crontab -e

```

Alternatively you could add a VISUAL environment variable in your $HOME/.bashrc:
```

export VISUAL=gedit

```

---

