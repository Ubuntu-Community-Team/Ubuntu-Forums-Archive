---
title: "Running Python scripts in Ubuntu"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by KeremE on 2011-06-04
Hey, I just made the switch to Ubuntu, but was wondering how to run Python scripts in Terminal? I know that 'python3.2 script.py' will run the program, but what if I want to test specific functions within the program?
In IDLE, the interpreter would allow me to define variables and call functions separately after I run the module (F5). Is there a way I can do that in Terminal?

---

### Post by SavageWolf on 2011-06-04
Just add "#!/usr/bin/python" to the top of the file (Without quotes), set the file as executable in the properties window thing and double click.

---

### Post by papibe on 2011-06-04
If you start your scripts with this:
```
#!/usr/bin/python
...
```
you can run them directly on the command line:
```
$ ./script.sh
```
But first you have add execution permissions:
```
$ chmod a+x script.py
```
Does it help?
Regards.

---

### Post by ExileAmongYou on 2011-06-04
I think what you might want is the python interpreter. Just type 'python' in the terminal without any filenames or scripts, and you'll get a python console that you can type individual lines into.

---

### Post by KeremE on 2011-06-04
Thanks for the replies!

@papibe and SavageWolf: I believe these methods allow me to run the program like python script.py would, but I'm not sure how to call methods from within terminal like this? Also, out of curiosity, why is the './' necessary before calling the executable file? Is this just convention?

@ExileAmongYou: I think that's what I'm looking for, but I can't figure out how to actually run files from within the interpretor? When I used IDLE in Windows, I could just open the code from IDLE and run the module using f5, but how do I run it here? According to some guides, it seems as if it is 'execfile script.py', but the interpreter says that execfile is not defined?

---

### Post by ExileAmongYou on 2011-06-04
I'm not sure if I understand exactly what you want. Opening the interpreter in the terminal will allow you to copy and paste individual lines of codes or functions from the script, if you have the script open in a text editor like gedit (you can also use the python console that's built into gedit, look in the plugins menu).
 I think to then run the whole script, you'd be better off opening another terminal window and doing what you've been doing previously, i.e. 'python script.py'.
You could also try installing an IDE like Geany, which might be more like what you're looking for.

---

### Post by KeremE on 2011-06-04
Sorry for the really bad explaining, but this is what I'm trying to do:

If I had a file foo.py like this

```

#!/usr/bin/python
print 'This is foo.'

def afunction(a,b):
    print 'This is the sum of a+b: ', a+b

```

Then I would like to be able to run not the entire file from Terminal (thus printing 'This is foo') but also be able to call afunction(2,5) from Terminal. Or to be able to set a=2 and b=5 in Terminal, then call afunction(a,b) and have it print 'This is the sum of a+b: 7'

---

### Post by ExileAmongYou on 2011-06-04
OK, that's what I thought. You're probably better off doing this entirely using gedit/Text Editor then. Here's how:
Open the python script in Gedit, you might have to right click on it and choose Open with->Text Editor.
In Gedit, go to Edit->Preferences->Plugins and turn on the Python console.
Open the Python Console by going to View->Bottom Pane.

Now you can copy and paste any functions you've defined in the script into that console and define new variables, and then call the functions from within the console. If you had any import statements at the top of the file that the functions depended on, you'd have to paste them in first.

---

### Post by Miljet on 2011-06-04
The reason for using "./" before calling a script is that, unlike Windows, *nix doesn't begin a search for the executable file in the current directory. It only searches what is listed in the path statement. Therefore the ./ just tell it to look in the current directory.

---

### Post by KeremE on 2011-06-04
Thanks! I have been trying to learn how to use Emacs, so it would be nice if there is a way to do that with Emacs (knowing Emacs, there probably is - time to Google). However, with gedit, is there also a way just to run the entire file as well? Using the steps in ExileAmongYou's post, I now know how to call afunction(a,b), but how do I just run foo.py in the console? Do I need to start Terminal and run 'python foo.py'?

---

### Post by mtiday on 2013-04-24
With the text editor of your choice create the Python program and save it with a .py extension. From the terminal type "python FileName.py" This will run the program from the terminal.

---

### Post by wildmanne39 on 2013-04-24
Old thread closed!

---

