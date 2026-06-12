---
title: "Interesting Terminal Command"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by merlin_ie on 2010-08-30
Hi everyone. I'm hoping someone can help with this question. I came across the following code in someone's sig ```
ruby -ne '$_.gsub(/<[^>]*>|\([^)]*\)|\[[^\]]*\]/,"").each_char{|i|STDOUT.flush.print(i);sleep(0.03)}if/(<\/li>|<ul>)<li>/' <(wget -qO- is.gd/e3EGx)
```
and when put in terminal, it reads about half of the following webpage : [http://en.battlestarwiki.org/wiki/Hybrid_utterances]("http://en.battlestarwiki.org/wiki/Hybrid_utterances")

I'm just trying to figure out how this works and would it be simple enough to implement to read say a document on my desktop. Any help would be greatly appreciated

---

### Post by Calash on 2010-08-30
I can not say how it works as i am not familiar with the code.

However you just committed a very dangerous action.  There are commands out there that look similar to what you posted that can cause serious damage to your computer.

Please see the following

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

Never never NEVER run a command unless you know what you are doing.

---

### Post by migs73 on 2010-08-30
+1 to Calash. If it looks like gibberish its probably trying to hide something.

---

### Post by Rubi1200 on 2010-08-30
+1 to both Calash and migs73

I have also seen, on occasion, interesting "code" posted in people's signatures.

If I don't know what it is, or does, there is only one thing to do; run away as quickly as I can!

As the link posted by Calash shows, seemingly "innocent" code can wreak havoc with your system.

Personally, I think if you see code like this again you should either ask the person what it does or report them to the admins.

Just my opinion.

---

### Post by Bachstelze on 2010-08-30
It just uses wget to fetch the page then does some regex magic on it.

---

### Post by merlin_ie on 2010-08-30
> **Bachstelze said:**
> It just uses wget to fetch the page then does some regex magic on it.

well, would there be a way to make it read a file from my desktop as I'm not always piped to internet and I'm just looking to try a few ideas

and to everyone else, I REALLY appreciate the warnings, but believe me, I don't run codes just for the heck of it. I have an ancient pc that I've been using for just mucking about with a 10gb hard-drive so if anything were to happen, I really wouldnt care. but again, thank you all for warnings

---

### Post by Bachstelze on 2010-08-30
Sure, just replace the last part (after the < sign) with the name of the file you want to dump.  Depending on the structure of the file, though, the needed regex magic migt be different.

---

### Post by merlin_ie on 2010-08-30
well, I'm thinking just html / txt files. but to be honest, I'm thinking to MAYBE try and pipe the output to conky somehow (like a fortune) but make it type like it does in terminal. But I just want to see how code works first

---

