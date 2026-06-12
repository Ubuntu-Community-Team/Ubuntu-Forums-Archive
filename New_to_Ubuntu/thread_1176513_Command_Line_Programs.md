---
title: "Command Line Programs"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Jolzath on 2009-06-02
I was wondering if Ubuntu had kept any of the Command Line programs, such as mail or pico.

---

### Post by Celauran on 2009-06-02
pico is actually just a link to nano now. mail is not installed by default.

---

### Post by Jolzath on 2009-06-02
> **Celauran said:**
> pico is actually just a link to nano now. mail is not installed by default.

Does Ubuntu have a page foretelling all of the Command Line Programs?

---

### Post by cariboo on 2009-06-02
Mail is enableb when you install an MTA such as exim4.

---

### Post by bodhi.zazen on 2009-06-02
> **Jolzath said:**
> I was wondering if Ubuntu had kept any of the Command Line programs, such as mail or pico.

There are tons of command line programs. What are you looking for ?

---

### Post by Boondoklife on 2009-06-02
> **Jolzath said:**
> Does Ubuntu have a page foretelling all of the Command Line Programs?

While at the command line you can press tab twice and it will give you a list of commands that are in your path, some may not be cli apps but give it a try.

---

### Post by mbsullivan on 2009-06-02
> I was wondering if Ubuntu had kept any of the Command Line programs, such as mail or pico.

For many command line programs, you must install them from the repositories, but it is simple.

> Does Ubuntu have a page foretelling all of the Command Line Programs? 

If there's a popular command-line program, Ubuntu will have it in its repos. Just search around on Google to see what you want.

Mike

---

### Post by Fundamental Unity on 2009-06-02
You can go to the page [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") to search for the package you are looking for.  Then when you find the package name, ```
sudo apt-get install [package-name]
``` will let you install it.

For a GUI experience, use the Synaptic Package Manager under the System->Administration menu.  The search bar there seems a little weaker than the web-site.  (For example, a search on gmp does not turn up libgmp3-dev.)  However, it is faster because everything is all in one place.

Specifically for "mail", you can install mailutils

```
sudo apt-get install mailutils
```

For "pico", you can install alpine-pico

```
sudo apt-get install alpine-pico
```

---

### Post by Jolzath on 2009-06-02
I am looking for, back when I had Linux a long time ago, able to look at mail, internet, file editing, compiling, etc all in the command line.

---

### Post by Cypher on 2009-06-02
```

sudo apt-get install mail elinks vi build-essential

```

---

### Post by Jolzath on 2009-06-02
> **Cypher said:**
> ```

sudo apt-get install mail elinks vi build-essential

```

couldn't find mail or vi. I got elinks though

---

### Post by Celauran on 2009-06-02
> **Jolzath said:**
> couldn't find mail or vi. I got elinks though

mail is mailx, vi is vim (and installed by default)

---

### Post by Jolzath on 2009-06-02
> **Celauran said:**
> mail is mailx, vi is vim (and installed by default)
Ah, thank you. Now how to configure mailx

---

### Post by Celauran on 2009-06-02
I don't know that it's particularly configurable, though you may want to take a peek at [this](http://www.opengroup.org/onlinepubs/009695399/utilities/mailx.html). If you're looking for a configurable command-line MUA, you're likely better off with mutt.

---

### Post by Jolzath on 2009-06-02
mutt looks better XD Now to configure that

---

### Post by kukibird1 on 2009-06-02
> **Jolzath said:**
> mutt looks better XD Now to configure that

The folllowing have been a big help for me.

[http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap]("http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap")


[http://www.therandymon.com/woodnotes/mutt/using-mutt.html]("http://www.therandymon.com/woodnotes/mutt/using-mutt.html")

[http://www.mutt.org/doc/manual/]("http://www.mutt.org/doc/manual/")

---

### Post by MrWES on 2009-06-02
> **Celauran said:**
> I don't know that it's particularly configurable, though you may want to take a peek at [this](http://www.opengroup.org/onlinepubs/009695399/utilities/mailx.html). If you're looking for a configurable command-line MUA, you're likely better off with mutt.

I love mutt -- I use that on my server install.

Bill

---

### Post by Girya on 2009-06-02
mutt works great. this how to works for ubuntu: [http://ubuntuforums.org/showthread.php?t=1021746]("http://ubuntuforums.org/showthread.php?t=1021746")

---

### Post by mbsullivan on 2009-06-02
A couple other great CLI/ncurses programs: Midnight Commander (for file browsing, copying, etc.) and rtorrent (BitTorrent client).

Also, if you're doing this all through a virtual terminal (no X running), don't forget that you can use a screen multiplexer (like "screen") to run multiple programs at the same time.

Mike

---

