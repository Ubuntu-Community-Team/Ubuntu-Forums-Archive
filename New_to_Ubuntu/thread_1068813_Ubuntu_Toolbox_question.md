---
title: "Ubuntu Toolbox question"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Xoanan on 2009-02-13
Hi All

I have been studying _Ubuntu Linux Toolbox_ by Christopher Negus and Francois Caen and I have some questions regarding sed in Chapter 5. (I may have more questions by the time I am done, of course).

In this chapter, they went over manipulating text, using various editors, grep, sed etc.  In one sed example, they said that quotes and back slashes are needed to escape the foward slashes to make sure they are not misinterpreted. 

Example ```
sed 's/\/home\/bob/\/home2\/bob/g' < /etc/passwd
```

What would happen if the quotes and backslashes were not there?

This may help me to understand it better.

Thanx

Xoanan:popcorn:

---

### Post by Xoanan on 2009-02-13
> **Xoanan said:**
> Hi All

I have been studying _Ubuntu Linux Toolbox_ by Christopher Negus and Francois Caen and I have some questions regarding sed in Chapter 5. (I may have more questions by the time I am done, of course).

In this chapter, they went over manipulating text, using various editors, grep, sed etc.  In one sed example, they said that quotes and back slashes are needed to escape the foward slashes to make sure they are not misinterpreted. 

Example ```
sed 's/\/home\/bob/\/home2\/bob/g' < /etc/passwd
```

What would happen if the quotes and backslashes were not there?

This may help me to understand it better.

Thanx

Xoanan:popcorn:
I figured it out on my own, this time;  w/o the quotes, and backslashes(or other delimiters), sed would replace /home  with /bob, which would not be so good.  Thanx!

---

