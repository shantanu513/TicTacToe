# TicTacToe
This game consists of 2 players , with tournament of 3 rounds . The one who wins atleast 2 rounds will be declared as the winner of the game.

//CODE 

import java.util.Scanner;

public class TictacToe {

	static void print(char arr[][]) {                   // TO PRINT THE BOARD
		for(int i=0;i<arr.length;i++) {
			for(int j=0;j<arr[0].length;j++) {
				System.out.print("|"+arr[i][j]+"| ' ");
			}
			System.out.println();
			System.out.println("----------------");
		}
	}
	
	static boolean checkIfWins(char arr[][]) { // TO CHECK IF THE PLAYER WINS
		 
		//FOR HORIZONTAL ROWS 
		
		for(int i=0;i<arr.length;i++) {         //IF player1Wins==3 , THEN PLAYER 1 WINS
			int player1Wins=0,player2Wins=0;    //IF player2Wins==3 , THEN PLAYER 2 WINS
			for(int j=0;j<arr[0].length;j++) {
				if(arr[i][j]=='X') {
					player1Wins+=1;
				}else if(arr[i][j]=='O') {
					player2Wins+=1;
				}
				if(player1Wins==3 || player2Wins==3) {
					return true;	
				}
			}
		}
		
		//FOR VERTICAL COLUMNS
		
		for(int i=0;i<arr[0].length;i++) {      //IF player1Wins==3 , THEN PLAYER 1 WINS
            int player1Wins=0,player2Wins=0;    //IF player2Wins==3 , THEN PLAYER 2 WINS
			for(int j=0;j<arr.length;j++) {
				if(arr[j][i]=='X') {
					player1Wins+=1;
				}else if(arr[j][i]=='O') {
					player2Wins+=1;
				}
				if(player1Wins==3 || player2Wins==3) {
					return true;
				}
			}
		}

		// FOR 1ST DIAGONAL FOR PLAYER 1
		
		if((arr[0][0]=='X' && arr[1][1]=='X') && (arr[2][2]=='X')) {
			return true;
		}
		
		// FOR 1ST DIAGONAL FOR PLAYER 2
		
		if((arr[0][0]=='O' && arr[1][1]=='O') && (arr[2][2]=='O')) {
			return true;
		}
		
		//i j
		//0 0
		//1 1
		//2 2
		
		// FOR 2ND DIAGONAL FOR PLAYER 1 
		
		if((arr[0][2]=='X' && arr[1][1]=='X') && (arr[2][0]=='X')) {
			return true;
		}
		
		// FOR 2ND DIAGONAL FOR PLAYER 2
		
		if((arr[0][2]=='O' && arr[1][1]=='O') && (arr[2][0]=='O')) {
			return true;
		}
		
		return false;
		//i j
		//0 2
		//1 1
		//2 0
	}
	
	static void insertInPos(char arr[][],int pos,int k) { // INSERT VALUE IN POSITION
		switch(pos) {
		case 1 : if(k % 2==0) {
			     arr[0][0]='X';
			     break;
		         }else {
		        	 arr[0][0]='O';
		        	 break;
		         }
		case 2 : if(k % 2==0) {
		         arr[0][1]='X';
		         break;
	             }else {
	        	 arr[0][1]='O';
	        	 break;
	         }
		case 3 : if(k % 2==0) {
		         arr[0][2]='X';
		         break;
	             }else {
	         	 arr[0][2]='O';
	        	 break;
	         }
		case 4 : if(k % 2==0) {
		         arr[1][0]='X';
		         break;
	             }else {
	        	 arr[1][0]='O';
	        	 break;
	         }
		case 5 : if(k % 2==0) {
		         arr[1][1]='X';
		         break;
	             }else {
	        	 arr[1][1]='O';
	        	 break;
	         }
		case 6 : if(k % 2==0) {
		         arr[1][2]='X';
		         break;
	             }else {
	        	 arr[1][2]='O';
	        	 break;
	         }
		case 7 : if(k % 2==0) {
		         arr[2][0]='X';
		         break;
	             }else {
	        	 arr[2][0]='O';
	        	 break;
	         }
		case 8 :if(k % 2==0) {
		         arr[2][1]='X';
		         break;
	             }else {
	        	 arr[2][1]='O';
	        	 break;
	         }
		case 9 :if(k % 2==0) {
		         arr[2][2]='X';
		         break;
	             }else {
	        	 arr[2][2]='O';
	        	 break;
	         }
		default : System.out.println("Please Provide Proper Input");
		          break;
		}
	}
	
	static void takeInput() {  // TAKE INPUT 
		
		
		Scanner sc=new Scanner(System.in);
		System.out.println("Enter Player 1 Name :");
		String player1=sc.nextLine();
		System.out.println("Enter Player 2 Name :");
		String player2=sc.nextLine();
		
		int pos=0;
		
		int roundNo=1,countPlayer1=0,countPlayer2=0;
		
		while(roundNo <= 3) {
			
		char arr[][]=new char[3][3];
			
		if(roundNo==1) {
	    	System.out.println("ROUND 1 STARTS");
	    }else if(roundNo==2) {
			System.out.println("ROUND 2 STARTS");
		}else if(roundNo==3) {
			System.out.println("FINAL ROUND STARTS");
		}
		
		
		for(int k=0;k<9;k++) {
			
		  if(k%2==0) {  // FOR PLAYER 1 , k==EVEN
			  
				System.out.println("Enter the Postion : ");
				pos=sc.nextInt();
				
				if(pos < 1  ||pos>9) {
					System.out.println("Please Enter Valid Input");
					break;
				}
				
				insertInPos(arr,pos,k);  // IF K IS EVEN THEN PLAYER 1 WILL PLAY 
				                         // HENCE PLAYER 1 WILL PLAY 5 TIMES
				
				print(arr);
				
				boolean ans=checkIfWins(arr); // CHECK IF PLAYER 1 WINS
				
				if(ans) {
					System.out.println(player1+" IS THE WINNER OF THIS ROUND");
					System.out.println();
					countPlayer1+=1;
					break;
				}
				
		  }else {  // FOR PLAYER 2, k==ODD
				   
				System.out.println("Enter the Postion : ");
				pos=sc.nextInt();
				
				if(pos < 1  || pos > 9) {
					System.out.println("Please Enter Valid Input");
					break;
				}
				
				insertInPos(arr,pos,k);// IF K IS ODD THEN PLAYER 2 WILL PLAY
				                       // HENCE PLAYER 2 WILL PLAY 4 TIMES
				
				print(arr);
				
				boolean ans=checkIfWins(arr); // CHECK IF PLAYER 2 WINS
				
				if(ans) {
					System.out.println(player2+" IS THE WINNER OF THIS ROUND");
					System.out.println();
					countPlayer2+=1;
					break;
				}
			}
		}
		
		System.out.println(roundNo+" ROUND OVER ");
		System.out.println();
		
		if((roundNo ==2) && (countPlayer1==2 || countPlayer2==2)) {
			break;
		}
		
		roundNo+=1;
		
	}
		if(countPlayer1>countPlayer2) {
			System.out.println(player1+" WINS THE TOURNAMENT");
			System.out.println();
			System.out.println(player2+" BETTER LUCK NEXT TIME");
		}else if(countPlayer2>countPlayer1) {
			System.out.println(player2+" WINS THE TOURNAMENT");
			System.out.println();
			System.out.println(player1+" BETTER LUCK NEXT TIME");
		}else {
			System.out.println("TOURNAMENT IS TIED NO-ONE IS THE WINNER");
			System.out.println();
			System.out.println("BETTER LUCK NEXT TIME "+player1+" AND "+player2);
		}
		
	}
	
	public static void main(String[] args) {
		takeInput();	

	}

}

