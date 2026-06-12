---
title: "Downloading from a URL using C on Ubuntu"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by hraja on 2010-04-18
Hello,

Since I'm relatively new to Ubuntu, I was wondering if someone could give me some help in opening a URL in C sourcecode.

I have to download an XML file from a URL in one of my programs and save it on disk.

I tried with the following code.Although this does not really download anything,I tried the following to atleast have the webiste running on my browser.Unfortunately I am unable to even do this. 

#include <stdio.h>
#include <stdlib.h>

void main()
{
system("\\usr\\lib\\firefox-3.5.8\\firefox  http://www.google.com");
}

Any help would be much appreciated.

Thanks very much.

---

### Post by spillin_dylan on 2010-04-18
> **hraja said:**
> Hello,

Since I'm relatively new to Ubuntu, I was wondering if someone could give me some help in opening a URL in C sourcecode.

I have to download an XML file from a URL in one of my programs and save it on disk.

I tried with the following code.Although this does not really download anything,I tried the following to atleast have the webiste running on my browser.Unfortunately I am unable to even do this. 

#include <stdio.h>
#include <stdlib.h>

void main()
{
system("\\usr\\lib\\firefox-3.5.8\\firefox  http://www.google.com");
}

Any help would be much appreciated.

Thanks very much.

I'm no C programmer at all, but I think I see two things wrong here.  

```

void main()
{
system("/usr/bin/wget http://www.google.com/")
}

```

I think that the backslashes should be regular forward slashes.
Try using [[COLOR="Blue"]wget[/COLOR]]("http://en.wikipedia.org/wiki/Wget") to download URLS instead of Firefox, or alternatively [[COLOR="Blue"]curl[/COLOR]]("http://en.wikipedia.org/wiki/CURL").

---

### Post by mellort on 2010-04-18
Hey hraja,

The Ubuntu Forums is not really the best place to ask programming questions. Personally, I think that [Stack Overflow]("http://www.stackoverflow.com") is a more appropriate website for that.

Regarding your question, it looks like [this question]("http://stackoverflow.com/questions/1636333/download-file-using-libcurl-in-c-c") on Stack Overflow answers what you are trying to do.

Cheers

---

