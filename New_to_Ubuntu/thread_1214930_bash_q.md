---
title: "bash q"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by carrarin on 2009-07-16
This going to sound weird, so bear with me. 
Have you ever seen anything at the terminal where they will do some weird little animation thing. 

For example. They will have this bar that will spin -- its really just the / | \ - charecters shown in the same spot on the terminal. 

I was wondering how this is done. 

im writing a chess program in c and i would like to have the output and game play look somewhat professional. ie, i don't want to have several printed repressentations on the board on my terminal. 
Is this clear enough? if it isn't just ask ! thank you

---

### Post by mcduck on 2009-07-16
I've never done it, but as backspace is a printable character like any other I'd assume that you print the first character of the animation, wait a bit, then print backspace and the second character, wait a bit then backspace and third character and so on.

But if you are going to print the whole board on terminal I don't think you'd want to use backspaces to erase it. Perhaps the "clear" command would do the trick?

edit: Of course you could also use carriage return to get back to the beginning of each line and print your new board in the same place that way..

Anyway, "echo \b" prints backspace and "echo \r" prints carriage return. "\c" suppresses newline, if you need to.

---

### Post by sisco311 on 2009-07-16
> **mcduck said:**
> I've never done it, but as backspace is a printable character like any other I'd assume that you print the first character of the animation, wait a bit, then print backspace and the second character, wait a bit then backspace and third character and so on.


yep

```
echo -n 1 && sleep 1 && echo -ne '\b' && echo -n 2 && sleep1 && echo -ne '\b' && echo -n 3 && sleep 1 && echo -ne '\b' && echo -n 4 && sleep 1 && echo -ne '\b' && echo -n 5
```

edit:
@OP: 

take a look at ncurses: [http://invisible-island.net/ncurses/ncurses.faq.html]("http://invisible-island.net/ncurses/ncurses.faq.html")

---

### Post by carrarin on 2009-07-16
I was thinking that i would use c for my program...

if i did something like

void loop(){
 int i;
 for(i = 0; i < 10000; i++){}
}

int main(){
 
 printf( "Hello World" ); // or printf( "%s" , "Hello World" )

 loop()

 printf( "%c", '\b' );
}


would my result on the screen be "Hello worl"

---

