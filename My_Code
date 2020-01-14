
#include <iostream>
#include <fstream>
#include <vector>


// DO NOT CHANGE THIS FILE.

template <class T>
class BSTNode {
public:
    T data;
    BSTNode<T> *left;
    BSTNode<T> *right;

    BSTNode();
    BSTNode(T data, BSTNode<T> *left, BSTNode<T> *right);

    template <class U>
    friend std::ostream &operator<<(std::ostream &os, const BSTNode<U> &obj);
};

template <class T>
BSTNode<T>::BSTNode() {

    this->left = NULL;
    this->right = NULL;
}

template <class T>
BSTNode<T>::BSTNode(T data, BSTNode<T> *left, BSTNode<T> *right) {

    this->data = data;
    this->left = left;
    this->right = right;
}

template <class T>
std::ostream &operator<<(std::ostream &os, const BSTNode<T> &obj) {

    os << obj.data;
    return os;
}


template <class T>
class BST {
public: // DO NOT CHANGE THIS PART.
    BST();
    BST(const BST<T> &obj);

    ~BST();

    BSTNode<T> *getRoot();

    void insert(const T &data);
    void remove(const T &data);
    BSTNode<T> *find(const T &data);
    void printInorder();

    BST<T> &operator=(const BST<T> &rhs);

private: // YOU MAY ADD YOUR OWN UTILITY MEMBER FUNCTIONS HERE.
    void printInorder(BSTNode<T> *node);
    void setRoot(BSTNode<T> *&r);
    void destruct(BSTNode<T> *&r);
    void copyTree(BSTNode<T> *&r, BSTNode<T> *objR);
    void inserthelper(BSTNode<T>* &r, const T &data);
    void DeleteNode(BSTNode<T>* &r, const T &data);
    BSTNode<T>* getMax(BSTNode<T> *&r);
    BSTNode<T>*  FindNode(BSTNode<T> *&r, const T &data);

private: // DO NOT CHANGE THIS PART.
    BSTNode<T> *root;
};


class IIData {
public:
    IIData();
    IIData(const std::string &word);

    std::string &getWord();
    std::vector<std::pair<std::string, std::vector<int> > > &getOccurrences();

    void setWord(const std::string &word);
    void setOccurrences(const std::vector<std::pair<std::string, std::vector<int> > > &occurrences);

    void addOccurrence(const std::string &documentName, int position);
    void removeOccurrences(const std::string &documentName);

    bool operator<(const IIData &rhs) const;
    bool operator>(const IIData &rhs) const;
    bool operator==(const IIData &rhs) const;

    friend std::ostream &operator<<(std::ostream &os, const IIData &data);

private:
    std::string word;
    std::vector<std::pair<std::string, std::vector<int> > > occurrences;
};

IIData::IIData() {

}

IIData::IIData(const std::string &word) {

    this->word = word;
}

std::string &IIData::getWord() {

    return word;
}

std::vector<std::pair<std::string, std::vector<int> > > &IIData::getOccurrences() {

    return occurrences;
}

void IIData::setWord(const std::string &word) {

    this->word = word;
}

void IIData::setOccurrences(const std::vector<std::pair<std::string, std::vector<int> > > &occurrences) {

    this->occurrences = occurrences;
}

void IIData::addOccurrence(const std::string &documentName, int position)
{
        bool page_exists=0;
        for(int i=0; i<occurrences.size(); i++){
            if((occurrences.at(i)).first==documentName){
                page_exists=1;
                ((occurrences.at(i)).second).push_back(position);
                break;
            }
        }
        if(!page_exists){
            std::vector<int> numbers;
            numbers.push_back(position);
            std::pair<std::string, std::vector<int> > nwpair (documentName, numbers);
            occurrences.push_back(nwpair);
        }
    
}

void IIData::removeOccurrences(const std::string &documentName) {
   if(occurrences.empty()){ return;}
    else {
        for(int i=0; i< (int)occurrences.size(); i++){
            if((occurrences.at(i)).first==documentName){
                occurrences.erase(occurrences.begin()+i);
                break;
            }
        }
    }
}

bool IIData::operator<(const IIData &rhs) const {

    return word < rhs.word;
}

bool IIData::operator>(const IIData &rhs) const {

    return word > rhs.word;
}

bool IIData::operator==(const IIData &rhs) const {

    return word == rhs.word;
}

std::ostream &operator<<(std::ostream &os, const IIData &data) {

    os << "{";
    os << "word: " << data.word << ", ";
    os << "occurrences: [";
    for (unsigned int i = 0 ; i < data.occurrences.size() ; ++i) {
        os << "(";
        os << data.occurrences[i].first << ", ";
        os << "[";
        if (!data.occurrences[i].second.empty()) {
            for (unsigned int j = 0 ; j < data.occurrences[i].second.size() - 1; ++j) {
                os << data.occurrences[i].second[j] << ", ";
            }
            os << data.occurrences[i].second[data.occurrences[i].second.size() - 1];
        }
        os << "]";
        os << ")";
        if (i != data.occurrences.size() - 1) {
            os << ", ";
        }
    }
    os << "]";
    os << "}";

    return os;
}

class InvertedIndex {
public: // DO NOT CHANGE THIS PART.
    InvertedIndex();
    InvertedIndex(const InvertedIndex &obj);

    ~InvertedIndex();

    BST<IIData> &getInvertedIndex();

    InvertedIndex &addDocument(const std::string &documentName);
    InvertedIndex &removeDocument(const std::string &documentName);
    InvertedIndex &searchWord(const std::string &word);
    InvertedIndex &printInvertedIndex();

    InvertedIndex &operator=(const InvertedIndex &rhs);

private:
    void removedochelper(BSTNode<IIData> *&r, const std::string &documentName);

private: // DO NOT CHANGE THIS PART.
    BST<IIData> invertedIndex;
};



InvertedIndex::InvertedIndex(const InvertedIndex &obj) {

    this->invertedIndex = obj.invertedIndex; // uses operator= of BST
}


BST<IIData> &InvertedIndex::getInvertedIndex() {

    return invertedIndex;
}

InvertedIndex &InvertedIndex::addDocument(const std::string &documentName) {

    std::ifstream file(documentName.c_str(), std::ifstream::in);
    
    std::string word;
    
    for (int position = 1; (file >> word); ++position) {
        BSTNode<IIData> *theNode = invertedIndex.find(IIData(word));
        if(theNode){
            theNode->data.addOccurrence(documentName, position);}
        else{
            IIData top;
            std::vector<std::pair<std::string, std::vector<int> > > newoccurence;
            std::vector<int> numbers;
            numbers.push_back(position);
            std::pair<std::string, std::vector<int> > myPair (documentName, numbers);
            newoccurence.push_back(myPair);
            top.setOccurrences(newoccurence);
            top.setWord(word);
            invertedIndex.insert(top);
        }
    }

    file.close();

    return *this;
}
void InvertedIndex::removedochelper(BSTNode<IIData> *&r, const std::string &documentName){
    
    if(r->left && r->right){
        removedochelper(r->left, documentName);
        removedochelper(r->right, documentName);
        removedochelper(r, documentName);
    }
    else if(r->left){
        removedochelper(r->left, documentName);
        removedochelper(r, documentName);
    }
    else if(r->right){
            removedochelper(r->right, documentName);
            removedochelper(r, documentName);
    }
    else{
        if(r->data.getOccurrences().size()==1) {
            if (r->data.getOccurrences()[0].first==documentName) { //delete this node
                invertedIndex.remove(r->data);
            }
        else {r->data.removeOccurrences(documentName);}
        
    }
    
    
}

InvertedIndex &InvertedIndex::removeDocument(const std::string &documentName) {
     if(InvertedIndex.getRoot())
       {   BSTNode<IIData> *temp= InvertedIndex.getRoot();
           removedochelper(temp);
       }
       return *this;
}

InvertedIndex &InvertedIndex::searchWord(const std::string &word) {

    BSTNode<IIData> *theNode = invertedIndex.find(IIData(word));

    if (theNode == NULL) {
        std::cout << "The word \"" << word << "\" does not exist in inverted index." << std::endl;
    } else {
        std::cout << theNode->data << std::endl;
    }

    return *this;
}

InvertedIndex &InvertedIndex::printInvertedIndex() {

    invertedIndex.printInorder();

    return *this;
}

InvertedIndex &InvertedIndex::operator=(const InvertedIndex &rhs) {

    this->invertedIndex = rhs.invertedIndex; // uses operator= of BST

    return *this;
}

template <class T>
void BST<T>::setRoot(BSTNode<T> *&r){
    root=r;
}

template <class T>
void BST<T>::destruct(BSTNode<T> *&r)
{if (r){
        if(r->left && r->right) {
        destruct(r->left);
        destruct(r->right);}
        else if(r->left) {
        destruct(r->left);}
        else if(r->right){
destruct(r->right);}
        BSTNode<T> *nw=r;
        if(nw){delete nw;
        r=NULL;}
}}
template <class T>
void BST<T>::copyTree(BSTNode<T> *&r, BSTNode<T> *objR)
{
    if(objR == NULL){
        r=NULL;}
    else{
        BSTNode<T> *nw= new BSTNode<T>(objR->data,NULL,NULL);
        r=nw;
        copyTree(r->left, objR->left);
        copyTree(r->right, objR->right);
    }
}
template <class T>
BSTNode<T>*  BST<T>::FindNode(BSTNode<T> *&r, const T &data)
{
    if (!r) return NULL;
    else if (r->data == data) return r;
    else if(r->data > data) return FindNode(r->left, data);
    else if(r->data < data) return FindNode(r->right, data);
    else return NULL;
    
}
template <class T>
BSTNode<T>* BST<T>::getMax(BSTNode<T>* &r)
{   BSTNode<T>* current = r;
    while (current->right != NULL)
        current = current->right;
   return current;
}

template <class T>
void BST<T>::DeleteNode(BSTNode<T>* &r, const T &data)
{
if(data < r->data )  DeleteNode(r->left, data);
else if(data > r->data)  DeleteNode(r->right, data);
else if(data == r->data){
    if(r->left && r->right) {
            r->data = getMax(r->left)->data;
            DeleteNode(r->left, r->data);
    }
    else{
            if(r->left){
               BSTNode<T>* temp = r;
                if(r==root){  root=r->left;}
                else{ r=r->left;}
                delete temp;
            }
            else if(r->right){
                BSTNode<T>* temp = r;
                if(r==root){  root=r->right;}
                else{  r=r->right;}
                delete temp;
            }
            else if(!r->left && !r->right){
                BSTNode<T>* temp = r;
                if(r==root) root=NULL;
                delete temp;
                r=NULL;}
    }
}
}

template <class T>
void BST<T>::inserthelper(BSTNode<T>*&r, const T &data)
{
    if (data < r->data) {
            if(r->left) {inserthelper(r->left,data);}
            else{
                BSTNode<T>* nw = new BSTNode<T>(data,NULL,NULL);
                r->left=nw;
            }
        }
    else if (data > r->data) {
        if(r->right) {inserthelper(r->right,data);}
        else{
            BSTNode<T>* nw = new BSTNode<T>(data,NULL,NULL);
            r->right=nw;
        }
    }
}

template <class T>
BST<T>::BST() {
    root=NULL;
}

template <class T>
BST<T>::BST(const BST<T> &obj)
{   if(!obj.root) root = NULL;
    else{
        root=NULL;
        BSTNode<T> *nw= new BSTNode<T>(obj.root->data,NULL,NULL);
        root=nw;
        BSTNode<T>* temp=root;
        BSTNode<T>* temp2=obj.root;
        copyTree(temp->left, temp2->left);
        copyTree(temp->right, temp2->right);
    }
}

template <class T>
BST<T>::~BST() {
   if(root) {
        BSTNode<T>* temp=getRoot();
        destruct(temp);
        root=NULL;
    }
}

template <class T>
BSTNode<T> *BST<T>::getRoot() {
     if(root)return root;
    else return NULL;
}

template <class T>
void BST<T>::insert(const T &data) {
if (!root){
    BSTNode<T>* nw = new BSTNode<T>(data,NULL,NULL);
    root=nw;
}
else{
    BSTNode<T>* temp = root;
    inserthelper(temp,data);
    }
}

template <class T>
void BST<T>::remove(const T &data) {
    if(root) {
    BSTNode<T>* temp = root;
    DeleteNode(temp, data);}
}

template <class T>
BSTNode<T>* BST<T>::find(const T &data) {
    if(root) {
        BSTNode<T>* temp = root;
        return FindNode(temp, data);
        temp=NULL;}
    else return NULL;
}

template <class T>
void BST<T>::printInorder() {

    if (root == NULL) {
        std::cout << "{}" << std::endl;
    } else {
        std::cout << "{" << std::endl;
        printInorder(root);
        std::cout << std::endl << "}" << std::endl;
    }
}

template <class T>
void BST<T>::printInorder(BSTNode<T> *node) {

    if (node == NULL)
        return;

    printInorder(node->left);
    if (node->left) {
        std::cout << "," << std::endl;
    }
    std::cout << "\t" << node->data;
    if (node->right) {
        std::cout << "," << std::endl;
    }
    printInorder(node->right);
}

template <class T>
BST<T> &BST<T>::operator=(const BST<T> &rhs) {
    if(rhs.root){
      BSTNode<T>* temp = root;
      destruct(temp);
      root=NULL;
      BSTNode<T> *nw= new BSTNode<T>(rhs.root->data,NULL,NULL);
      root=nw;
      temp=root;
      copyTree(temp->left, rhs.root->left);
      copyTree(temp->right, rhs.root->right);
    }
    else{
        BSTNode<T>* temp = root;
        destruct(temp);
        root=NULL;}
    return *this;
}


int main(){
    InvertedIndex selin;
    std::fstream myfile;
    myfile.open ("the1.txt");
    myfile << "my name is Selin";
    myfile.close();
    selin.addDocument("the1.txt");
    selin.printInvertedIndex();
    return 1;
}
