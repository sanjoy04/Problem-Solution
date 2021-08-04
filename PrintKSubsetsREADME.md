# Print K subsets
/*1. You are given two integers n and k, where n represents number of elements and k represents 
     number of subsets.
2. You have to partition n elements in k subsets and print all such configurations
n=3
k=2
Sample Output
1. [1, 2] [3] 
2. [1, 3] [2] 
3. [1] [2, 3] */

import java.io.*;
import java.util.*;

public class Main {
    static int counter = 0;
	public static void solution(int i, int n, int k, int nos, ArrayList<ArrayList<Integer>> ans) {
		
		if(i>n){
		    if(nos==k){
		        counter++;
		        System.out.print(counter+". ");
		        for(ArrayList<Integer>set:ans){
		            System.out.print(set+" ");
		        }
		        System.out.println();
		    }
		    return;
		}
		
		for(int j=0; j<ans.size(); j++){
		    if(ans.get(j).size()>0){
		        ans.get(j).add(i);
		        solution(i+1, n, k, nos, ans);
		        ans.get(j).remove(ans.get(j).size()-1);
		    }else{
		        ans.get(j).add(i);
		        solution(i+1, n, k, nos+1, ans);
		        ans.get(j).remove(ans.get(j).size()-1);
		        break;
		    }
		}
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		ArrayList<ArrayList<Integer>> ans = new ArrayList<>();
		for(int i  = 0; i < k; i++) {
			ans.add(new ArrayList<>());
		}
		solution(1, n, k, 0, ans);

	}

}
