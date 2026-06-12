---
title: "Decrypting MD5 hash code"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-25
Just for learning purpose i would like to know...Is it possible to decrypt MD5 hash code?If so how?

---

### Post by 3rdalbum on 2010-03-25
> **getyourkarthick said:**
> Just for learning purpose i would like to know...Is it possible to decrypt MD5 hash code?If so how?

No. Hashing is a mathematical technique that cannot be reversed. That's why it's used for checking passwords - websites do not store your password, they hash your password and store that. Then when you enter your password into the website, your browser hashes the password and sends it to the website and it is checked against the hashed password that was stored earlier.

Or were you hoping to take the 16-character hash of the Ubuntu ISO and "decrypt" it into the 700 megabyte ISO? That would save on internet bills! Just hash the entire Internet, download the hash and then decrypt it on your computer!

---

### Post by HermanAB on 2010-03-25
Well, it is possible to compute a collision.  That is the case where you calculate a new password that happens to compute to the same MD5 hash.  

It is possible with MD5, but it would on average take an very, very long time to do so.

---

