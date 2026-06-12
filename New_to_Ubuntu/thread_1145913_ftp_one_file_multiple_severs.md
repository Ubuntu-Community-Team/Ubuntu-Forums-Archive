---
title: "ftp one file multiple severs?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2009-05-02
is there a way under Linux to download one file from multiple ftps at the same time ... you know to double my bandwidth

---

### Post by 3rdalbum on 2009-05-02
Not as far as I am aware, unless a command-line download manager like Aria supports it?

The best option for such transfers is Bittorrent, which does operate in this way.

---

### Post by m_duck on 2009-05-02
Yeah, aria supports it I think. ```
sudo apt-get install aria2
```To run it use it from the command line```
aria2c <url1> <url2> <url3>
```At least I think that's right... If not check the man page, it'll say there.

---

### Post by &lt;&lt;joe&gt;&gt; on 2009-05-02
wow thanks

---

