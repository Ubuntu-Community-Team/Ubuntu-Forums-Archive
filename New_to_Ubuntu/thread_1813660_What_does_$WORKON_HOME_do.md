---
title: "What does $WORKON_HOME do"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by flebber on 2011-07-28
I am reading docs [here]("http://pypi.python.org/pypi/pip") for python pip. Since I want to use it with virtualenv wrapper it advises to set $WORKON_HOME into my .bashrc . It doesn't really state what the result of that will be .

I was hoping that it would mean it would install the eggs into the subdirectory of the current active virtual environemnt.
```
~/.virtualenv/nameOfVenvInstall/ 
```

Does it do that? or is there a better command to have a nice accessible location for my eggs. It all started when I created a virtualenv to learn web2py. 
I switched using
```
workon learnWeb2py
```
after using pip to install web2py i went to issue the command
```
python web2py.py -S welcome
```

I found though i could not locate where pip installed the package. Suggestions?

---

### Post by androssofer on 2011-07-28
> **flebber said:**
> I am reading docs [here]("http://pypi.python.org/pypi/pip") for python pip. Since I want to use it with virtualenv wrapper it advises to set $WORKON_HOME into my .bashrc . It doesn't really state what the result of that will be .

I was hoping that it would mean it would install the eggs into the subdirectory of the current active virtual environemnt.
```
~/.virtualenv/nameOfVenvInstall/ 
```

Does it do that? or is there a better command to have a nice accessible location for my eggs. It all started when I created a virtualenv to learn web2py. 
I switched using
```
workon learnWeb2py
```
after using pip to install web2py i went to issue the command
```
python web2py.py -S welcome
```


I found though i could not locate where pip installed the package. Suggestions?


not 100% sure what your asking... are you wanting to know how to add the $WORKON_HOME to your enviroment variables? which could be the cause of any issues running CLI commands...

---

### Post by flebber on 2011-07-28
> **androssofer said:**
> not 100% sure what your asking... are you wanting to know how to add the $WORKON_HOME to your enviroment variables? which could be the cause of any issues running CLI commands...

Python with virtualenv wrapper. When working in a virtual environment one uses pip to install packages. However I installed web2py whilst in a virtualenv and was then unable to issue the below command because web2py.py file could not be found.
```
python web2py.py -S welcome
```

So I started looking at the virtualenv docs to see how to manage pip installed packages in a virtualenv. The docs say to better manage pip I may want to update ~/.bashrc with $WORKON_HOME.

But what will adding $WORKON_HOME do? How can I better manage my virtualenvs and the installs?

---

### Post by androssofer on 2011-07-28
> So I started looking at the virtualenv docs to see how to manage pip installed packages in a virtualenv. The docs say to better manage pip I may want to update ~/.bashrc with $WORKON_HOME.

But what will adding $WORKON_HOME do? How can I better manage my virtualenvs and the installs?

i see. sounds like enviroment variables! never worked with python, pip etc but i think i get the concept. 

$WORKON_HOME i assume would aim at the workon directory. for example i have $JAVA_HOME in my .bashrc which aims at /etc/java-6-openjdk  (the java directory). in .bashrc tht would look like:

```
$JAVA_HOME=/etc/java-6-openjdk
``` 

i will give an example of how i would update JAVA_HOME and you can apply it to WORKON_HOME...

so i would add tht to my $PATH so PATH knows where to look for java files. in my .bashrc it would look like:

```
$JAVA_HOME=/etc/java-6-openjdk
PATH=$PATH:$JAVA_HOME
export PATH
``` 

then if i installed sumthing within the java directory (an addon) i could add this to the $JAVA_HOME then export it all: .bashrc would look like:

```
$JAVA_HOME=/etc/java-6-openjdk
PATH=$PATH:$JAVA_HOME
$JAVA_ADDON=$JAVA_HOME/addonSubDirectory
PATH=$PATH:$JAVA_ADDON
export PATH
``` 

save and exit. then do:

```
source .bashrc
```

for it to take effect. thts an example using java, but yours would vary slightly... hope it helps u understand it... (this is the problem i assume ur having...)

---

### Post by flebber on 2011-07-28
Thanks for the explanation, so what i have done specific to python virtualenv is to add this to my .bashrc

```
export PIP_RESPECT_VIRTUALENV=true
WORKON_HOME=/home/sayth/.virtualenvs
export PIP_VIRTUALENV_BASE=$WORKON_HOME
```

Seems to be working for me currently, will see if any anomaly arises.

---

### Post by androssofer on 2011-07-29
> **flebber said:**
> Thanks for the explanation, so what i have done specific to python virtualenv is to add this to my .bashrc

```
export PIP_RESPECT_VIRTUALENV=true
WORKON_HOME=/home/sayth/.virtualenvs
export PIP_VIRTUALENV_BASE=$WORKON_HOME
```

Seems to be working for me currently, will see if any anomaly arises.

could perhaps change that to:

```
WORKON_HOME=/home/sayth/.virtualenvs
PATH=$PATH:$WORKON_HOME
export PATH
```

but thts me being fussy. if it works, u can leave it :-).

glad its workin now for ya.. 

+1 for the forums!

---

### Post by phenomenon.aurora on 2011-09-03
hey guys,
can you provide me the complete and proper ways to install virtualenv in ubuntu 11.04,
i need the complete steps and the bashrc changes to be made.
please help me

thanks
phenomenon

---

### Post by flebber on 2011-09-03
Well after playing around with things a bit this is my advice, oh firstly installing virtualenv you just use easy_install, my advice however is to use pythonbrew.

Pythonbrew will allow you to manage your python installs and keep them clean/managed separate from your system install. Pythonbrew also includes a wrapper to virtualenv. Install is very simple and docs found here [https://github.com/utahta/pythonbrew#readme]("https://github.com/utahta/pythonbrew#readme")

From the docs its then this easy to create projects using virtualenv.
```
Create isolated python environments (uses virtualenv):

pythonbrew venv init
pythonbrew venv create proj
pythonbrew venv list
pythonbrew venv use proj
pythonbrew venv delete proj
```

---

