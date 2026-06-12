---
title: "Beginer in C programing + openGL"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by xyznanixyz on 2009-11-16
Hi, I am an absolute beginer in programming. I'm trying to use the openGL

The task is simple,to draw a polygon in a new window.

sorce code : 

#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#include<GL/gl.h>
#include<GL/glut.h>
.

void display(void)  
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT); 
    glColor3f(1.0f, 0.0f, 0.0f); 
    glBegin(GL_POLYGON);  
        glVertex2f(0.0, 0.0);
        glVertex2f(0.0, 3.0);
        glVertex2f(4.0, 3.0);
        glVertex2f(6.0, 1.5);
        glVertex2f(4.0, 0.0);
    glEnd();
    glutSwapBuffers();
}


int main(int argc, char**argv)            
{
  glutInit(&argc, argv);
  glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB);
  glutInitWindowSize(300, 300);            
  glutInitWindowPosition(100, 100);         
  glutCreateWindow("Mnogokotnik");         
  glutDisplayFunc(display);              
  glutMainLoop();                     
           
return 0;
}

after compiling the return is : 

- a black window and a 

freeglut (./vaja133): Unable to create direct context rendering for window 'Mnogokotnik'
This may hurt performance.


any ideas ?  

THX

---

