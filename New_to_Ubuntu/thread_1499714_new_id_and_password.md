---
title: "new id and password"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by retro-rocket on 2010-06-02
i,m a newbe i,m want to create a new id and password so it,s a bit more secure just for my internet banking etc, can any one help ??

---

### Post by ThesaurusRex on 2010-06-02
Assuming you have root privileges, there are a couple of ways. The quickest is through the terminal:

sudo useradd "username"
sudo passwd "username"

Where "username" is of course the username you want. You'll be prompted to give a password after the second command.

---

### Post by lisati on 2010-06-02
You can do it with System->Administration->Users and groups

---

### Post by nhasian on 2010-06-02
you can do it with one command by specifying the password with the -p switch

```
sudo useradd username -p password
```

> **ThesaurusRex said:**
> sudo useradd "username"
sudo passwd "username"


---

### Post by SoFl W on 2010-06-02
Do you want to do this for the bank, or for your use on ubuntu?

---

### Post by ThesaurusRex on 2010-06-02
> **SoFl W said:**
> Do you want to do this for the bank, or for your use on ubuntu?

But if it was for the bank, wouldn't it just be done from a website these days?

---

### Post by SoFl W on 2010-06-02
> **ThesaurusRex said:**
> But if it was for the bank, wouldn't it just be done from a website these days?

Yes.  That is why I was a little confused.  I wasn't sure if he was asking how to come up with a unique and secure username and password* for* his bank or weather he wanted an account on ubuntu to use just for online banking.   (I am still trying to wake up)

---

### Post by retro-rocket on 2010-06-02
i,m wanting a seperate id and pass on ubuntu  to use just for online banking and a few other sites

---

### Post by ThesaurusRex on 2010-06-02
> **retro-rocket said:**
> i,m wanting a seperate id and pass on ubuntu  to use just for online banking and a few other sites

In that case, we're leading you in the right direction. Any progress?

---

