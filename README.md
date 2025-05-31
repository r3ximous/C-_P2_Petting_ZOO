# C-_P2_Petting_ZOO
This C# application helps organize animals in a petting zoo for school visits. It randomly distributes animals into groups to ensure each school visit offers a unique experience.

Core Features
Animal Management
The program maintains a collection of 18 different animals available in the petting zoo, including alpacas, capybaras, chickens, and more.

Randomization
Using the RandomizeAnimals() method, the program implements a Fisher-Yates shuffle algorithm to randomly reorder the animals before each school visit:

void RandomizeAnimals() 
{
    Random random = new Random();

    for (int i = 0; i < pettingZoo.Length; i++) 
    {
        int r = random.Next(i, pettingZoo.Length);

        string temp = pettingZoo[r];
        pettingZoo[r] = pettingZoo[i];
        pettingZoo[i] = temp;
    }
}

Group Assignment
The AssignGroup() method divides animals into a configurable number of groups (default: 6):

string[,] AssignGroup(int groups = 6)
{
    string[,] result = new string[groups, pettingZoo.Length / groups];
    int start = 0;

    for (int i = 0; i < groups; i++)
    {
        for (int j = 0; j < result.GetLength(1); j++)
        {
            result[i, j] = pettingZoo[start++];
        }
    }

    return result;
}

Visit Planning
The PlanSchoolVisit() method orchestrates the entire process for a school visit:

Randomizes the animal order
Assigns animals to groups
Prints the resulting groups with the school name
Usage
The program can plan multiple school visits with different group configurations:

PlanSchoolVisit("School A");            // Default: 6 groups
PlanSchoolVisit("School B", 3);         // 3 groups
PlanSchoolVisit("School C", 2);         // 2 groups

Each visit results in a different random distribution of animals, ensuring variety across different school visits.

Output
For each school visit, the program outputs:

The school name
A numbered list of groups
The animals assigned to each group
This allows teachers and zoo staff to easily coordinate which animal groups students will visit during their field trip.
