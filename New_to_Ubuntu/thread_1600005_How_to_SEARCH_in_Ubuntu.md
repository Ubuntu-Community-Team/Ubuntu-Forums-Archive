---
title: "How to SEARCH in Ubuntu?"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by arcelivez on 2010-10-18
Hello,

1) can anybody tell me how do I search in folder or, for example I need to find a song in my newly inserted USB flash drive... So I tried search but it doesn't work I tried writing more advanced expressions like *othing*ompares* in the search file, but still, no luck, it doesn't find anything. All I need is for it to find a single mp3, like it does when I search in Windows... :(

2) Hmm, of course it would also be good to know if more advanced search options are also available in Ubuntu? Like the file indexing in Windows 7? Is that possible in Ubuntu? I use the app Desktop Search, but if I add too many places to index it will be slow again? So how do I ...?

Please at least answer question no.1 for now... Thanks in advance.

Arturas

---

### Post by Joshwaa on 2010-10-18
Places -> Search for Files..

---

### Post by Sealbhach on 2010-10-18
For a very specific search I would use the locate command in the terminal.

If I was looking for "nothing compares" I would just do

```
locate compares
```

That will be likely to find it. If it's something you've added recently to your filesystem, I would update the database first by running
```

sudo updatedb
```

That update happens automatically every day, so you can find most things without having to update.

---

### Post by sikander3786 on 2010-10-18
Beagle is another powerful search tool.

[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)

---

### Post by arcelivez on 2010-10-18
Thanks guys,

especially for the search for files. I somewhat originally thought that it would be like in windows: in Nautilus there is a binocular icon, i thought that would be it, but it seems it's very different here. :D Thanks, never came to the idea of opening that.

Uhm thanks for the locate command, I'll try it out sometime.

And for Beagle desktop search, I do use it as I've mentioned it, but guess I'll have to to play with it's settings sometime.

Thanks again. :)

---

### Post by arcelivez on 2010-10-18
And Hell yeah, it does seem to work really fast with the USB flash drive

---

