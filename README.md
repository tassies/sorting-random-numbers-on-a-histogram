# sorting-random-numbers-on-a-histogram
For any random numbers that are generated, the program must sort them according to the range give n and construct a histogram

#include iostream

#include ctime

#include cstdlib

#include vector

#include algorithm

using namespace std;

//this variables can be accessed from by any function within this project

int oneToTen, tenToTwenty, TwentyToThirty,thirtyToFourty, fourtyToFifty = 0;

int fiftyToSixty, sixtyToSeventy, SeventyToEighty, eightyToNinety, ninetyToHundred = 0; 

/**Generate random numbers for the users given range
  return : random number
*/

int RandomNumber(int startPoint,int endPoint)
{
   
     int number = 0;
   
    number = rand() % (endPoint - startPoint -1) ;
    
    return number;

}

/**fill vector with integer values, for a given interval
   return : vector array
*/

vector<int> PopulateVector(int vecSize,int startPoint,int endPoint)
{

    int numbers = 0;
    
    vector<int> vectorArray;

    vectorArray.reserve(vecSize);

    for(int i = 0; i < vecSize; i++)
    {
    
        numbers = RandomNumber(endPoint,startPoint);
        
        vectorArray.push_back(numbers);// sort vector using sort function as shown below...
        
    }

    std::sort(vectorArray.begin(), vectorArray.end());//sort vector from small to large
    
    return vectorArray;
    
}

/**Find mode value 
   return : mode
*/

int MostAppearingValue(vector<int> myVector)
{
 
    int mostOccur = myVector[1];
    
    int tempMost =0;
    
    int counter = 0;
    
    int currentElement = 0;
    
    //iterate vector from 0 to size -1, to avoid index out of bounds error
    
    for(int i = 0;i < myVector.size();i++)
    {
    
      tempMost = myVector[i]; //set current vector element to tempMost

      counter = 0;// initialise counter to zero

      for(int j = 0; j < myVector.size();j++)//iterate vector from 0 to size, this to
      {                                     
       // be able to compare element and count

        if(tempMost == myVector[j])//current temp number is equals to the current element in vector
      {                          
      
      // increment counter

      counter++;

      }
    }
    
    if(tempMost > counter)//check if we found the current highest counter
    {
    
     mostOccur = tempMost;

     counter = tempMost;
    
    }
  }
    
    return mostOccur;//return value with most appearance

}

/**Calculate mean Value
return : mean
*/

int CalculateMean(vector<int> myVector)
{

  int mean = 0;

  int sum = 0;

  for(int i = 0; i < myVector.size(); i++)
  {

   sum += myVector[i];//add all the elements in vector

  }

 mean = sum / myVector.size();//divide the sum of by the size/number of items in vector

 return mean;

}

/**Calculate Median Value and return : median */

int MiddleValue(vector<int> myVector)
{
 
   //sort

   (myVector.begin(),myVector.end(),"");

   int midValue = myVector.size() / 2;

   /**this to place the midValue in the middle of the vector*/

   /**Check if length of Vector is even or odd*/

   if(myVector.size() % 2 == 0)
    {

      /**if vector size is even, there is no middle*/

      /**so we return the position*/

      return (myVector[midValue -1] + myVector[midValue]) / 2;
    }

     else
     {

      /**odd size, subtract 1 from the middle, the add the*/

      return myVector[midValue];

     }
  }

  /**Count the number of values within a specified range*/
  

  void CountNumberOfAppearance(vector<int> myVector)
  {

   for(int currentV : myVector)

  {

  if(currentV > 0 && currentV <= 10)
  {

   oneToTen++;

  }

   else if(currentV > 10 &&  currentV <= 20)
   {

   tenToTwenty++;

   }

   else if(currentV > 20 &&  currentV <= 30)
   {

   TwentyToThirty++;

   }

   else if(currentV > 30 &&  currentV <= 40)
   {

   thirtyToFourty++;

   }

   else if(currentV > 40 &&  currentV <= 50)
   {

   fourtyToFifty++;

   }

   else if(currentV > 50 &&  currentV <= 60)
   {

   fiftyToSixty++;

   }

   else if(currentV > 60 &&  currentV <= 70)
   {

    sixtyToSeventy++;

   }

   else if(currentV > 70 &&  currentV <= 80)
   {

    SeventyToEighty++;

   }

   else if(currentV > 80 &&  currentV <= 90)
   {

    eightyToNinety++;

   }

   else if(currentV > 90 &&  currentV <= 100)
   {

    ninetyToHundred++;

   }
  }
 }

   /**Display Histogram*/

void DisplayHistogram(vector<int> myVector)
{

   //use for loop to be able to count from 0 to value of the range counted

   cout<<"[001, 010]: ";

   for(int i = 0; i < oneToTen;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[011, 020]: ";

   for(int i = 0; i < tenToTwenty;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[021, 030]: ";

   for(int i = 0; i < TwentyToThirty;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[031, 040]: ";

   for(int i = 0; i < thirtyToFourty;i++)
   {

     cout<<"* ";

   }

   cout<<endl;

   cout<<"[041, 050]: ";

   for(int i = 0; i < fourtyToFifty;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[051, 060]: ";

   for(int i = 0; i < fiftyToSixty;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[061, 070]: ";

   for(int i = 0; i < sixtyToSeventy;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[071, 080]: ";

   for(int i = 0; i < SeventyToEighty;i++)
   {

    cout<<"* ";

   }

   cout<<endl;

   cout<<"[081, 090]: ";

   for(int i = 0; i < eightyToNinety;i++)
   {

    cout<<"* ";

   }

  cout<<endl;

  cout<<"[091, 100]: ";

  for(int i = 0; i < ninetyToHundred;i++)
  {

    cout<<"* ";

  }

  cout<<endl;

}

  /**Call the functions to find the mean
                                    mode
                                    median
  */

void DisplayMeanModeMedian(vector<int> myVector)
{

   //display mean

   cout<<"Vector Mean is: "<<CalculateMean(myVector)<<endl;

   //display the most appearing value in histogram

   cout<<"Most Appearing value is: "<<MostAppearingValue(myVector)<<endl;

   //display median

   cout<<"Middle Value in Vector is: "<<MiddleValue(myVector)<<endl;

}

int main()
{

   int startPoint = 0;

   int endPoint = 0;

   int vectorSize = 0;

   vector<int> myVector;

   cout<< "enter Start point "<<endl;

   cin >> endPoint;

   cout<< "enter End point "<<endl;

   cin>> startPoint;

   if((startPoint<1)||(endPoint>100))
   {

   RandomNumber(endPoint=100,startPoint=1);

   }

   cout<< "enter vectorSize "<<endl;

   cin>> vectorSize;

   cout<< "Array Size is: " << vectorSize<<endl;

   //assign the returned (populated) vector to local vector

   //this so we can only have one vector across the entire project

   //with consistent data

   myVector = PopulateVector(vectorSize,startPoint,endPoint);

   //display elements in vector

   for(int vectorElement : myVector)
   {

    cout<<"My Vector Var is: "<< vectorElement <<endl;

   }

   //display mean, median and mode

   DisplayMeanModeMedian(myVector);

   //count the number of time a number within a range is found in vector

   CountNumberOfAppearance(myVector);

   //display histogram

   //pass parameter vector of type int

   DisplayHistogram(myVector);

   return 0;

}
