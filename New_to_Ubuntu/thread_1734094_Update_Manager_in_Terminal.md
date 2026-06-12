---
title: "Update Manager in Terminal"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Giraffemonster on 2011-04-19
Hello, I've been thinking about the Update Manager in Ubuntu. The repository management software in Ubuntu slows down my computer, and runs very slowly. Because of this, I try to install most of my programs via terminal (with apt-get install or dpkg -i) I'm not exactly sure how I would install the packages like the Update Manager would in the terminal though.

Just two questions.

1. Would using sudo apt-get update be the same as running package manager? If not, what would be the same?

2. How can I make it so that every day, Ubuntu starts up the terminal with that command instead of starting the Update Manager?

Distribution is Ubuntu Desktop Edition 10.10 32-bit, system specs are in my sig, thanks.

---

### Post by taseedorf on 2011-04-19
It's pretty much the same, yes.

As for the start up, create a script that loads at boot.

just make it an executable bash script and turn off update manager.

so, in a text file write
#!/bin/bash 
sudo apt-get update
sudo apt-get upgrade


save it as update.sh
and do chmod +x update.sh
then use startup manager to have it autorun

---

### Post by Giraffemonster on 2011-04-19
I made the file, and it tested it. It ran successfully and I could see it scanning through the repositories, and I set it up to start every day.

One thing I noticed though is that the script automatically shuts down the terminal after it runs. Is that intended?

Thanks again. No longer will my system slow to a crawl on those occasions. :D

---

### Post by idi0tf0wl on 2011-04-19
> **Giraffemonster said:**
> 
One thing I noticed though is that the script automatically shuts down the terminal after it runs. Is that intended?


Yup.

---

