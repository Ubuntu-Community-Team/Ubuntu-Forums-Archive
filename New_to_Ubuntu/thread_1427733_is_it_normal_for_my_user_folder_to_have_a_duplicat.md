---
title: "is it normal for my user folder to have a duplicate (see pic)"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by hanzj on 2010-03-11
So I was using my computer today, and I got a message saying that I'm low on hard drive space. I clicked the "Examine" tab and "Disk Usage Analyzer" popped up. Please tell me whether it's normal to have my user directory copied twice. Please see attached cropped screenshot.

"sevenup" folder is under home/.ecryptfs/.Private
and it's also in /home/

---

### Post by alfplayer on 2010-03-11
Is your home directory encrypted?

---

### Post by hanzj on 2010-03-11
Yes, I think I encrypted it.

---

### Post by alfplayer on 2010-03-11
> **hanzj said:**
> Yes, I think I encrypted it.

That's probably the reason.

---

### Post by whoop on 2010-03-11
the one with the "." is the actual data, the one without the "." is the decrypted mount.

---

### Post by hanzj on 2010-03-11
So if I understand you all correctly, encrypted stuff means a doubling of data. Wow.

---

### Post by alfplayer on 2010-03-11
> **hanzj said:**
> So if I understand you all correctly, encrypted stuff means a doubling of data. Wow.

The data stored on the hard drive is not doubled. The data read from the encrypted directory is decrypted on-the-fly (as it is being read by a program), and the data to be written on the encrypted directory is, obviously, being encrypted (also on-the-fly, as programs write on the directory).

---

### Post by hanzj on 2010-03-11
So only the currently needed data is decrypted? If so why is there an almost exact match in size. (54.9 vs 54.8 GB)?

---

### Post by alfplayer on 2010-03-11
> **hanzj said:**
> So only the currently needed data is decrypted? If so why is there an almost exact match in size. (54.9 vs 54.8 GB)?

Yes. It appears doubled so that programs can access encrypted **and** decrypted data (normally they only access the decrypted data).

---

### Post by hanzj on 2010-03-11
alfplayer,
you wrote "It appears doubled..."

By "appear" do you mean it's not *really *doubled?

---

### Post by alfplayer on 2010-03-11
> **hanzj said:**
> alfplayer,
you wrote "It appears doubled..."

By "appear" do you mean it's not *really *doubled?

Exactly. It's doubled on-the-fly, only what is being accessed, that is, not permanently, and not entirely. I'm sure there is a lot of info about data encryption on the web.

---

