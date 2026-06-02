# arvore


#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    char dado;
    struct No *esquerdo;
    struct No *direito;
} No;

No* criarNo(char valor) {
    No *novoNo = (No*) malloc(sizeof(No));
    novoNo->dado      = valor;
    novoNo->esquerdo  = NULL;
    novoNo->direito   = NULL;
    return novoNo;
}


void emOrdem(No *no){
	
	if (no != NULL){
		
		emOrdem(no->esquerdo);
		printf("%c ", no->dado);
		emOrdem(no->direito);
	}
	
}


int main() {
    No *noA = criarNo('a');
    No *noB = criarNo('b');
    No *noC = criarNo('c');
    No *noD = criarNo('d');
    No *noE = criarNo('e');

    No *noDivisao = criarNo('/');
    noDivisao->esquerdo = noC;
    noDivisao->direito  = noD;

    No *noSubtracao = criarNo('-');
    noSubtracao->esquerdo = noDivisao;
    noSubtracao->direito  = noE;

    No *noMultiplicacao = criarNo('*');
    noMultiplicacao->esquerdo = noB;
    noMultiplicacao->direito  = noSubtracao;

    No *raiz = criarNo('+');
    raiz->esquerdo = noA;
    raiz->direito  = noMultiplicacao;

    printf("Expressao em ordem simetrica:\n");
    emOrdem(raiz);

    return 0;
}
