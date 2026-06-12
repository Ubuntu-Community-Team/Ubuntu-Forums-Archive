---
title: "Java program doesn't function in ubuntu"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by Degran on 2011-08-07
Some java applications that I made while I used Vista don't work in Ubuntu. They worked perfectly in Windows and if I make some changes to the code they work again.
In vista I used netbeans and in ubuntu I've tried netbeans and eclipse. I've got the openJDK java 6 runtime and use ubuntu 11.04.

When buttons are pressed the value of the 'case' field of the window is changed and the text of that button is changed.
The main class checks the field and performs an action depending on the value. It then changes the value to the standard 0 and changes the text through a method.

```

public static void main (String[] args){
        
        Window            win        = new Window();
        
        while(true)
        {
            if(win.getCase()==1){
                try{
                    RenameShuffle.shuffle(new File(win.getDir()));
                }catch(Exception exc){}
                
                win.unpress();
            }
            else if(win.getCase()==2){
                try{
                    RenameShuffle.revert(new File(win.getDir()));
                }catch(Exception exc){}
                
                win.unpress();
            }    
        }
        
    }//main

```The unpress() method changes the value to 0 and changes the texts.
When the event causes the actions to be performed and not the change of the field everything works fine. 

The strange thing is that the text of the button changes after the button is pressed but no action is performed and the text is never changed back. When I check the value of 'case' it's already 0 which should be impossible because the only way to make it 0 is the unpress() method.
Another weird thing is that when I run the code slowly in debug mode by placing breakpoints it does work.
It looks like the value of 'case' is set to 0 before the Main class can check it.

I know this isn't the best way to program this but I was wondering why this doesn't work.

---

### Post by xpasaway on 2011-08-07
hi..

im wondering whats the purpose of that program? what is your intention or what are u trying to figure out?

thanks.

---

### Post by Degran on 2011-08-08
I've experienced this problem with two programs. The second one using code from the first. Both of the programs rename files to change their alphabetical order. The code shown here is from a program that puts a random number before the name to shuffle files in a folder. The other calculates a common substring of all the filenames in a folder and renames them to be sorted by the next two numbers that follow that substring. (I use this to sort episodes of series)

Since the problem seems to be caused by the interface and I can solve it by making changes to only the main and window class, I didn't think it really mattered what the programs do but I'm willing to provide more info if it helps clarify this issue :)

---

