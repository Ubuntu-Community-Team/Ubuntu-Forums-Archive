---
title: "cat laid on keyboard and now wireless not recognized"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by thinkpeace on 2008-01-28
I am trying this post again.

My cat laid down on my laptop keyboard, and now I don't list any wireless networks.  I have tried to follow the troubleshooting guides, but I have a limited knowledge of linux.  Do I have to reload a driver?  or maybe is there a way to check to see if the wireless card is working?

Please help.

thanks

---

### Post by .nedberg on 2008-01-28
A lot of laptops have a shortcut for turning the wireless on and off. On my Dell machines it is Fn+F2. Try and see if there is a button like that on your keyboard.

Hope you solve it!

Else;
```

cat wireless > /dev/null

```

Sorry, could not resist that one :lolflag:

---

### Post by thinkpeace on 2008-01-28
I had tried that already too. maybe I didn't wait long enough before trying something else.  This time, I pressed function+A symbole thing and waited, and maybe 20 seconds later, it finally started to show some activity.

Thanks a lot.

by the way, since I don't speak in linux code (yet), what would happen to my cat if I used the command you put in?

---

### Post by .nedberg on 2008-01-28
That was, in fact, a joke in bash language.

cat is a command to "Concatenate FILE(s), or standard input, to standard output." It shows the content of a file. Read more [here]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cat")

/dev/null is a device, often used to send output into oblivion. Read more [here]("http://en.wikipedia.org/wiki/Data_sink")

So the command would send the content of a file named wireless to /dev/null

But I was just making fun of your cat problem.

Glad you fixed the problem though!

---

