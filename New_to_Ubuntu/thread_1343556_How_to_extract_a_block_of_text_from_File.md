---
title: "How to extract a block of text from File?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2009-12-02
I currently use nmap to send to an output file.  I am currently grepping "Interesting" to let me know which IPs have ports open.  Currently I am only able to grab the line.

What I would like to be able to do is grab a section that starts with Interesting and ends with seconds.  (Regardless of how many lines it has in it)  Does anyone know how to do it? AWK?

Example:

eric@ctsg-desktop:~$ nmap 127.0.0.1

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-12-01 21:21 PST
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds

eric@ctsg-desktop:~$ cat nmap.file | grep Interesting
Interesting ports on localhost (127.0.0.1):

Want to send command which grabs for each match in the file:

Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds

---

### Post by diesch on 2009-12-02
```
nmap 127.0.0.1| awk '/^Interesting/,/seconds$/'
```

---

### Post by u.b.u.n.t.u on 2009-12-02
diesch,

Good work!

[http://www.florian-diesch.de/](http://www.florian-diesch.de/)

---

### Post by J0hnnyBr@v0 on 2009-12-02
Thank you!! (Danke Schon)

Works like a charm!  But I am sure you already knew that! ;-)

---

### Post by J0hnnyBr@v0 on 2009-12-02
diesch,

Ich arbeite auf einem Python-Skript für nmap. Ich versuche, die Logger-get-Funktion arbeiten. Können Sie einige mögliche Erkenntnisse gewonnen? Würden Sie zu sehen, das Skript interessiert?

---

### Post by u.b.u.n.t.u on 2009-12-02
> **J0hnnyBr@v0 said:**
> diesch,

Ich arbeite auf einem Python-Skript für nmap. Ich versuche, die Logger-get-Funktion arbeiten. Können Sie einige mögliche Erkenntnisse gewonnen? Würden Sie zu sehen, das Skript interessiert?

Wow, rather good German there! Mine is as rusty as a 14th century tall-ship nail!

"I am working on a Python script for nmap. I'm trying to get the logger working function. Can you win some possible findings? Would you see, are interested in the script?"

* translated  by Google.

Being an English language forum, a translation is applicable.

---

### Post by J0hnnyBr@v0 on 2009-12-02
> **u.b.u.n.t.u said:**
> Wow, rather good German there! Mine is as rusty as a 14th century tall-ship nail!

"I am working on a Python script for nmap. I'm trying to get the logger working function. Can you win some possible findings? Would you see, are interested in the script?"

* translated  by Google.

Being an English language forum, a translation is applicable.

Sorry...only did the German for diesch ;-)

Trying to get the logger function working in my Python script.  Have done a workaround to get it going.  Wanted to see if diesch had any advise, or wanted to see it.

meant no harm...

Eric

---

### Post by u.b.u.n.t.u on 2009-12-02
Hey it's cool. He seems a good person to ask. I was complementing you on your language skills.

---

