---
title: "Listener not working"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by xrsox on 2011-05-10
Hi,

Im new here... I'm programming a Game in Java but I don't know why the KeyListener is not working correctly... Here are the 2 classes that are involved with the listener.

**public class Tablero extends JPanel**
{
	public JFrame ventana;
	public Casilla tablero[][];
	private Personaje pers;
	
	
	public Tablero (JFrame v)
	{
		ventana = v;
		leeFichero();
		
		
		System.out.println ( "Termina de leer el fichero!" );
		
		JPanel panel = new JPanel();
		panel.setLayout( new GridBagLayout() );
		GridBagConstraints propsLayout = new GridBagConstraints();
		propsLayout.gridx = 0;
		propsLayout.gridy = 0;
		propsLayout.gridwidth = 1;
		propsLayout.gridheight = 1;
		propsLayout.fill = GridBagConstraints.BOTH;
		propsLayout.weightx = 1.0;
		propsLayout.weighty = 1.0;
		
		//Coloco el personaje en el tablero
		
		pers = new Personaje ( "./Imagenes/personaje.png",40,40 );
		
		panel.add ( pers, propsLayout );
		
		//Pinto el tablero
		
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				panel.add( tablero[i][j], propsLayout );
			}
		}
		
		System.out.println ( "Escenario pintado!" );
		
		v.setContentPane(panel);
		
		**[SIZE="3"]v.addKeyListener ( new Listener(this) );[/SIZE]**
		
		v.setSize ( 617, 640 );
		v.setLocationRelativeTo ( null );
		v.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		v.setVisible(true);
		
	}
@Override
	public void paintComponent ( Graphics g )
	{
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				tablero[i][j].update(g);
			}
		}
		pers.update(g);
	}
	
	public void muevePersonajeIzquierda()
	{
		//Miro cual es la posición actual del personaje
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		System.out.println (" Entra al muevePersonajeIzquierda() ");
		
		if ( !tablero[posYact][posXact-1].Llena() )
		{
			pers.mueveIzquierda();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeDerecha()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact][posXact+1].Llena() )
		{
			pers.mueveDerecha();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeArriba()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact-1][posXact].Llena() )
		{
			pers.mueveArriba();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeAbajo()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact+1][posXact].Llena() )
		{
			pers.mueveAbajo();
			ventana.repaint();
		}
	}
	
	public void leeFichero()
	{
		String f = "./Ficheros/Escenario.txt";
		
		try
		{
			BufferedReader br = new BufferedReader ( new FileReader(f) );
			String cadena = br.readLine();
			
			//Leo la primera linea donde estan el numero de filas y columnas y
			//el tamaño de las casillas
			int cuantasX = (new Integer ((cadena.split(","))[0])).intValue();
			int cuantasY = (new Integer ((cadena.split(","))[1])).intValue();
			int medidaCasilla = (new Integer(((cadena.substring(1)).split(","))[2])).intValue();
			
			
			tablero = new Casilla[cuantasX][cuantasY];
			
			for ( int i = 0; i < cuantasX; i++ )
			{
				cadena = br.readLine();
				
				
				String cas[] = cadena.split(" ");
				
				
				for ( int j = 0; j < cuantasY; j++ )
				{
					if ( j < cas.length )
					{
						try
						{
							//System.out.println ( "Integer.parseInt( cas[j]: "+Integer.parseInt( cas[j] ) );
							
							tablero[i][j] = new Casilla( Integer.parseInt( cas[j] ), j*medidaCasilla, i*medidaCasilla );
							
							//System.out.println( "tablero[i][j]: "+tablero[i][j] );
							
							
						}catch (Exception e)
						{
							tablero[i][j] = new Casilla();
						}
					}
				}
			}
			
			br.close();
			
		}
		catch(Exception e)
		{
			System.out.println("Error al leer el fichero:" +e.getMessage() );
		}
	}
	
	
	
}

import java.awt.event.*;


**public class Listener implements KeyListener**
{
	Tablero t;
	
	public Listener ( Tablero tab )
	{
		t = tab;
	}
	
	public void keyPressed ( KeyEvent e )
	{
		if ( e.getKeyCode() == KeyEvent.VK_LEFT )
		{
			t.muevePersonajeIzquierda();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_RIGHT )
		{
			t.muevePersonajeDerecha();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_UP )
		{
			t.muevePersonajeArriba();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_DOWN )
		{
			t.muevePersonajeAbajo();
		}
	}
	
	public void keyReleased ( KeyEvent e ){}
	
	public void keyTyped ( KeyEvent e ){}
	
}


Any ideas?? I need help :_(

---

### Post by compmodder26 on 2011-05-10
You'll likely find better help for this type of question in the programming forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by xrsox on 2011-05-10
> **compmodder26 said:**
> You'll likely find better help for this type of question in the programming forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

ok man... i'll try it there... thanks :D

---

