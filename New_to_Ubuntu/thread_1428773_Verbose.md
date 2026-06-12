---
title: "Verbose"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by IrishLad on 2010-03-13
I was wondering in terms of shell scripting what verbose means and how it functions? Is this the correct section to post these in.

---

### Post by victor.zamanian on 2010-03-13
Verbose usually means to output extra information as things are happening in a program. For example in the man page for the `cp' utility, the -v flag is described:

       -v, --verbose
              explain what is being done

So verbose mostly refers to output, and more of it. I don't know if this is what you are referring to---let me know if not. :)

---

### Post by IrishLad on 2010-03-13
> **victor.zamanian said:**
> Verbose usually means to output extra information as things are happening in a program. For example in the man page for the `cp' utility, the -v flag is described:

       -v, --verbose
              explain what is being done

So verbose mostly refers to output, and more of it. I don't know if this is what you are referring to---let me know if not. :)


Cool yeah I think it is, cheers :p, can you tell me is it only done by putting If statements with a read in variable when true echo, or is there a way of just telling the program to do it? Just the IF way seems to take alot of extra code so I tot maybe theres a quick way? Thanks again for your help.

---

### Post by victor.zamanian on 2010-03-13
Oh you are thinking of making your own shell script verbose if the user says it wants it to be? If so then yes I do believe you have to check every time and then specify what you want to output. This is what the programmers of programs must do as well. :)

Although, if you are using programs in your shell script, for example cp or rm, or something else that can be verbose on its own, then you won't really need to use echo, but just pass the flag to that particular program which will tell it to be verbose.

You might want to let your script take flags (also called arguments), in particular the "-v" flag which is often the flag chosen to make the program verbose.

There are some great tutorials on the web about bash scripting. You might for example be well off reading the following page:

[http://tldp.org/LDP/abs/html/internal.html#EX33](http://tldp.org/LDP/abs/html/internal.html#EX33)

---

### Post by IrishLad on 2010-03-13
> **victor.zamanian said:**
> Oh you are thinking of making your own shell script verbose if the user says it wants it to be? If so then yes I do believe you have to check every time and then specify what you want to output. This is what the programmers of programs must do as well. :)

Although, if you are using programs in your shell script, for example cp or rm, or something else that can be verbose on its own, then you won't really need to use echo, but just pass the flag to that particular program which will tell it to be verbose.

You might want to let your script take flags (also called arguments), in particular the "-v" flag which is often the flag chosen to make the program verbose.

There are some great tutorials on the web about bash scripting. You might for example be well off reading the following page:

[http://tldp.org/LDP/abs/html/internal.html#EX33](http://tldp.org/LDP/abs/html/internal.html#EX33)


Thanks very much, I knew the country that gave us Larsson wouldn't let me down LOL

---

### Post by victor.zamanian on 2010-03-13
No problem! :) lol, which of all the Larssons are you referring to? :D

---

### Post by IrishLad on 2010-03-13
> **victor.zamanian said:**
> No problem! :) lol, which of all the Larssons are you referring to? :D

The most important one, Henrik Larsson of course LOL

---

### Post by victor.zamanian on 2010-03-13
Hah! Right, figured that would be the one. ;)

Anyways good luck on your scripting. :D Feel free to look me up if you need more help. I'm far from an expert on shell scripting, though I have done some scripts before and I am a programmer so I might be able to at least fish out some info if you need it. No promises though. ;)

---

### Post by IrishLad on 2010-03-13
> **victor.zamanian said:**
> Hah! Right, figured that would be the one. ;)

Anyways good luck on your scripting. :D Feel free to look me up if you need more help. I'm far from an expert on shell scripting, though I have done some scripts before and I am a programmer so I might be able to at least fish out some info if you need it. No promises though. ;)

Thats excellent thanks very much, and I hope I won't have to bend your ear too much :p

---

### Post by victor.zamanian on 2010-03-13
No problem! I'm sure you'll do fine on your own, you seem like a capable chap. ;)

---

