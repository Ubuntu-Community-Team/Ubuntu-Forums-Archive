---
title: "Forward slash problem"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Ignorance Isnt Bliss on 2011-04-13
I have a problem with my keyboard, forward slash, left arrow and up arrow, don't work all of a sudden. When I use the question mark and pgup on these keys using shift and function keys they don't work either. 

I am using an eeepc which has had Ubuntu installed for almost 3 years with no problems I am using Lucid 10.04.

I am pretty sure it's a software problem because I haven't dropped my computer or done anything unusual. Might have been caused by a software update but I don't know which one or how to reverse it.

Can anyone help me solve this problem. I am not sure how to report it as a bug if that is what this is.

Thanks in advance

---

### Post by Nickjpost on 2011-04-13
When you use the keys that work, are they correct? ex-you press 'q' and q will be the output?

---

### Post by HermanAB on 2011-04-13
Howdy,

I have experienced nonsense like that in the past on my EeePC, where the T key suddenly went haywire.  It is a problem with Xorg, but why it happened, remained a total mystery.  It could be indicative of a failure of the SSDD.

In then end, I used xmodmap to remap the keys at startup.  Here is a guide that describes how xmodmap and xev work:
"http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/"

That guys used xmodmap to disable a key, but you can use the same method to assign it (to itself - to what it is supposed to be).

Hope that helps!

---

### Post by Ignorance Isnt Bliss on 2011-04-13
Thanks for both replies. 

NickJPost yes all other keys do as they are supposed to.

HermanAB Thanks for your reply will read the guide and see if it isn't too complex for me. Also I don't want to make things worse. Sounds a bit like treating the symptoms rather than the disease but so long as the keyboard works that isn't a problem.

---

