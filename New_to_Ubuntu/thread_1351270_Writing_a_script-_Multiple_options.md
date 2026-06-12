---
title: "Writing a script- Multiple options"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Defiant Rat on 2009-12-10
So, im trying to write a script where the user has multiple options for what they want to do. This is what ive tried:
```
echo -n "Do you want to run command a (a), command b (b) or none (n) > "
read
if [ "$REPLY" = "a" ]; then
    echo "command a"
if [ "$REPLY" = "b" ]; then
    echo "Command b"
else
fi
```When i run it and select an option i get:
```
line 19: syntax error: unexpected end of file
```So what do i need to change? Or am i doing it totally wrong?

Thanks.

EDIT, This works:
```
echo -n "Do you want to run command a (a), command b (b) or none (n) > "
read
if [ "$REPLY" = "a" ]; then
    echo "command a"
elif [ "$REPLY" = "b" ]; then
    echo "Command b"
else
fi
```Thanks anyway ;)

---

### Post by lavinog on 2009-12-18
you can remove the else statement

---

