---
title: "Having problem with Sudoers"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by juil on 2010-09-18
I've been following the tutorial here:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

I get stuck in the beginning at 'Editing the sudoers file' subheading. 
As you can see from the screenshot, I have appended 

```
export EDITOR=nano
```

Then when i ran 
```
source ~/.bashrc
```
it gave me the error as shown in screenshot.

Then i ran
```
sudo -E visudo
```

but it wont allow me to type anything. What am i doing wrong?

---

### Post by scorchgeek on 2010-09-18
I'm assuming from the command name that this command uses VI as its text editor. VI has an unusual control scheme which I won't go into detail about, but basically:
1. Use the h,j,k,l keys to scroll where you want to go
2. Press i to begin inserting before current letter.
3. Type what you want to add.
4. Press ESC to get out of insert mode.
5. Type :wq to save and exit.

If you screwed up, you can hit escape a couple of times and type :q! to exit without saving.

See this website if you need help on more vi commands:
```
http://www.cs.colostate.edu/helpdocs/vi.html
```

---

### Post by CharlesA on 2010-09-18
Yup. It's using vi.

Hit the insert key to start adding text, hit it again to replace text.

Hit esc to go back where you can use commands.

To write changes, type: ":w"
To quit, type: ":q"

---

### Post by juil on 2010-09-18
Thanks so much guys! 
It worked beautifully. I'm guessing ubuntu team was assuming that you would know how to use vi. 
But how would an absolute beginner know that vi was not a simple text editor and needs to execute different commands, if it's not in the documentary?
They should at least put a small sentence in there saying something like: 'You would have to know how to use vi in order to add this line.'
Anyway, problem solved. Thanks guys!

---

### Post by scorchgeek on 2010-09-18
I do agree that's a little odd--other tools like crontab let you choose what editor to use and point you to nano as the easiest.

But so what, you got it working. :)

---

### Post by CharlesA on 2010-09-18
That's why it's called "visudo."

;)

---

