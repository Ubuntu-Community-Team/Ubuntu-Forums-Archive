---
title: "Could anybody help with a bit of java please?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by lewbram on 2008-12-17
Hi
I was just wandering if there is anybody out there who knows a bit of java, that could maybe help me?

Thanks

lewbram

---

### Post by rlunger on 2008-12-17
> **lewbram said:**
> Hi
I was just wandering if there is anybody out there who knows a bit of java, that could maybe help me?

Thanks

lewbram

What specifically do you need?

---

### Post by lewbram on 2008-12-17
I have some coursework to do. I have managed some but have hit a wall when i am trying to call a method from another class.

when I click Circle Button I want it to draw the circle;
problems 
- the circle needs to be made visible and this needs to be true for the Shape_Maker class and I am not allowed to change the circle class or the canvas class.

public class Shape_Maker

.........


CircleButton = new Jbutton ("Circle");
    CircleButton.addActionHandler(new ActionListener(){
        public void actionPerformed(ActionEvent e){
             showCircle();
             }
        });




public void showCircle();
{
    Circle circle = Circle = get.Circle();
    circle.draw();
}
------------------------------------------------------------

public class Circle
 

.........

    public void draw()
    {
        if(isVisible) {
            Canvas canvas = Canvas.getCanvas();
            canvas.draw(this, color, new Ellipse2D.Double(xPosition, yPosition, 
                                                          diameter, diameter));


-----------------------------------------------------------

---

### Post by lewbram on 2008-12-17
oh I forgot the showCircle compiles but doesn't work either!

---

### Post by mrbiggbrain on 2008-12-17
im not that knowlegable about java, but i did see something that in c++ is legal, but verry naughty!

Circle circle <-- though in strongly typed languages such as c++ this compiles (as Circle and circle as well as cIrcle, circlE, are all diffrent variables, it makes your code MUCH harder to read, even by you, and becomes quite troublesom now, and impossible to read later.

i have no idea how java handles programing names, nor if it is strongly typed (will have errors not just warnings) however this is bad programing practice regardless of your language. 

id say change circle to something more manageable such as circle_circ1 or circ_circle1, or circ_2draw, ect. though it seems easier to --you--- right --now-- to just name it circle, thats what it is right? but to a programer as the code gets more confuseing, they are gonna be like, WTH does circle do? and whats the diffrence between circle and circle, and even situations where typeing "Circle" instead of "circle" may be legal, compile, and cause errors that are HARD as sin to find.

im not judgeing your programing style, i did the same thing, im trying to save you alot of headache when someday it catches up to you as it did me.

bad names

wheel w1;

good name

wheel wheel_front_left;

bad name

int amount;

good name

int int_pistol_ammo;

again, you can countiue as you do, i might be missing WHY you do it, but to me, it makes programing cleaner

---

### Post by lewbram on 2008-12-17
Thanks for the advice I will bear that in mind. 

I think I have a module in c++ next semester any other advice?

---

### Post by mrbiggbrain on 2008-12-17
> **lewbram said:**
> Thanks for the advice I will bear that in mind. 

I think I have a module in c++ next semester any other advice?

commenting is good in moderation. doing something without comments is a bad thing, but over commetning can be just as bad

// setting the value of broken_car to half working_car

broken_car = working_car / 2;

this might seem like a simple comment, but the statement itself implys your doing this. now im not saying dont use irrelivent comments, but dont clog a program with comments it dosnt need.

also make sure you pay attention and work hard at classes, they seem really hard at first, but when you get them, c++ finally makes sence!

---

### Post by jespdj on 2008-12-17
There's a [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum where this question belongs.

There are also other websites, such as [JavaRanch](http://www.javaranch.com), which have very good forums about Java programming. (I'm a moderator on JavaRanch).

---

### Post by dmizer on 2008-12-18
> **lewbram said:**
> I have some coursework to do.
Please do not post homework questions on this forum.

Thank you. :)

---

