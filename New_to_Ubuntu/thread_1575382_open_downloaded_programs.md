---
title: "open downloaded programs"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by N84Christ on 2010-09-15
I downloaded thunderbird email. How do i open it?

---

### Post by solar george on 2010-09-15
Please read the section of [http://ubuntu-manual.org/](http://ubuntu-manual.org/) about Software Management, in short it is almost always best to install software from Ubuntu's repos rather than downloading it directly from the developers.
To get thunderbird quickly just click [here]("apt://thunderbird"), doing so will act as a shortcut to allow you to install thunderbird from the official ubuntu package repositories.

---

### Post by t0p on 2010-09-15
It sounds to me like you've downloaded the *gzipped source code* for Thunderbird; to use Thunderbird, you must *install* it.  If you want to use the source code you downloaded, you'll need to *unzip* the *archive*, make sure you've got the package *build-essential* installed, then *compile* the source code so it will run on your computer.  [**Note:** everything above in *italics* is terminology that will help you in the long run to understand what in heck you're doing.  But there is an Easy Compiling guide available [here]("https://help.ubuntu.com/community/CompilingEasyHowTo").]

But, unless there is a pressing reason why you want the downloaded version of Thunderbird, you'll probably be better off just opening a terminal and typing

```

sudo apt-get install thunderbird

```

Thunderbird will then install over the internet, it will appear in the menu **Applications > Office** and you can customise it your needs.

Go the **sudo apt-get...** route.  So so so much simpler.

---

### Post by oldos2er on 2010-09-15
Right-click, extract here.

---

