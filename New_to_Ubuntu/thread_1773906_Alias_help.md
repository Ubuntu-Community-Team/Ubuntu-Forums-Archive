---
title: "Alias help"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Gamicon on 2011-06-02
I'm looking for a file that defines aliases available to all users? is this something that already exists, or is it something that I have to make?

I cant find a whole lot of specific help on aliases.

---

### Post by m_duck on 2011-06-02
Certain aliases will be set by default. You can see what is there by running the following command in the terminal:```
alias
```

To create a new alias, you need to add a line to your ~/.bashrc or a file that is sourced from there (assuming of course that you are using BASH):
```
alias my_alias_name='the command you want aliased'
```

These can be simple or more complex. For anything remotely complex though, you will probably want to use a function, defined in the same files as above.

---

### Post by jtarin on 2011-06-02
[There's more than one way to deal with aliases. ]("https://help.ubuntu.com/community/Sudoers") Maybe this will help. Scroll down.

---

