#include <stdio.h>
#include <string.h>

// Estrutura da carta
typedef struct {
    char estado[50];
    char codigo[20];
    char nome[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadePopulacional;
} Carta;

// Função para cadastrar a carta
void cadastrarCarta(Carta *carta, int num) {
    printf("\n=== Cadastro da Carta %d ===\n", num);
    printf("Estado: ");
    scanf(" %[^\n]", carta->estado);
    printf("Código: ");
    scanf(" %[^\n]", carta->codigo);
    printf("Nome da Cidade: ");
    scanf(" %[^\n]", carta->nome);
    printf("População: ");
    scanf("%d", &carta->populacao);
    printf("Área (km²): ");
    scanf("%f", &carta->area);
    printf("PIB (em bilhões): ");
    scanf("%f", &carta->pib);
    printf("Número de pontos turísticos: ");
    scanf("%d", &carta->pontosTuristicos);
    carta->densidadePopulacional = carta->populacao / carta->area;
}

// Exibe informações da carta
void exibirCarta(Carta carta, int num) {
    printf("\n--- Carta %d: %s (%s) ---\n", num, carta.nome, carta.estado);
    printf("Código: %s\n", carta.codigo);
    printf("População: %d\n", carta.populacao);
    printf("Área: %.2f km²\n", carta.area);
    printf("PIB: %.2f bilhões\n", carta.pib);
    printf("Pontos Turísticos: %d\n", carta.pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km²\n", carta.densidadePopulacional);
}

// Compara dois valores com base na regra
int compararAtributo(float valor1, float valor2, int atributo) {
    if (atributo == 4) {
        return (valor1 < valor2) ? 1 : (valor1 > valor2) ? 2 : 0;  // Menor vence
    } else {
        return (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;  // Maior vence
    }
}

// Retorna o valor do atributo escolhido
float getValorAtributo(Carta c, int op) {
    switch (op) {
        case 1: return c.populacao;
        case 2: return c.area;
        case 3: return c.pib;
        case 4: return c.densidadePopulacional;
        case 5: return c.pontosTuristicos;
        default: return -1;
    }
}

// Nome legível do atributo
const char* nomeAtributo(int op) {
    switch (op) {
        case 1: return "População";
        case 2: return "Área";
        case 3: return "PIB";
        case 4: return "Densidade Populacional";
        case 5: return "Pontos Turísticos";
        default: return "Desconhecido";
    }
}

int main() {
    Carta carta1, carta2;
    int atributo1, atributo2;

    printf("🔮 Sistema de Cartas – Nível Mestre 🔮\n");

    // Cadastro
    cadastrarCarta(&carta1, 1);
    cadastrarCarta(&carta2, 2);

    // Exibição
    exibirCarta(carta1, 1);
    exibirCarta(carta2, 2);

    // Menu de comparação dupla
    printf("\nEscolha o PRIMEIRO atributo para comparar:\n");
    printf("1 - População\n2 - Área\n3 - PIB\n4 - Densidade Populacional (MENOR vence)\n5 - Pontos Turísticos\n> ");
    scanf("%d", &atributo1);

    printf("Escolha o SEGUNDO atributo para desempate:\n> ");
    scanf("%d", &atributo2);

    // Obtem os valores
    float val1_c1 = getValorAtributo(carta1, atributo1);
    float val1_c2 = getValorAtributo(carta2, atributo1);
    float val2_c1 = getValorAtributo(carta1, atributo2);
    float val2_c2 = getValorAtributo(carta2, atributo2);

    // Comparação
    int resultado = compararAtributo(val1_c1, val1_c2, atributo1);

    printf("\n--- Resultado da Comparação ---\n");

    if (resultado == 1) {
        printf("🏆 %s venceu com base no atributo %s.\n", carta1.nome, nomeAtributo(atributo1));
    } else if (resultado == 2) {
        printf("🏆 %s venceu com base no atributo %s.\n", carta2.nome, nomeAtributo(atributo1));
    } else {
        printf("Empate no atributo %s. Usando %s como critério de desempate...\n",
               nomeAtributo(atributo1), nomeAtributo(atributo2));
        int desempate = compararAtributo(val2_c1, val2_c2, atributo2);

        if (desempate == 1) {
            printf("🏆 %s venceu no desempate com %s.\n", carta1.nome, nomeAtributo(atributo2));
        } else if (desempate == 2) {
            printf("🏆 %s venceu no desempate com %s.\n", carta2.nome, nomeAtributo(atributo2));
        } else {
            printf("🤝 Empate total! Nenhuma carta venceu.\n");
        }
    }

    return 0;
}
